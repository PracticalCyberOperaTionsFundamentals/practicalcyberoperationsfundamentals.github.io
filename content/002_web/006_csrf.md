---
title: CSRF
nav_order: 5
parent: Web
has_chidren: true
permalink: /web/csrf/
---

# What is CSRF
```
from flask import Flask, session, redirect, request, render_template_string, url_for, abort

app = Flask(__name__)
app.secret_key = "demo"

# A pretend “database”
USERS = {"alice": {"email": "alice@example.com", "balance": 1000}}

# ── helpers ─────────────────────────────────────────────────────────────────────
def current_user():
    username = session.get("user")
    return USERS.get(username)

# ── routes ──────────────────────────────────────────────────────────────────────
@app.route("/")
def index():
    user = current_user()
    if not user:
        return redirect(url_for("login"))
    return render_template_string("""
        <h1>Hi {{user}}!</h1>
        <p>Email on file: <b>{{data.email}}</b></p>
        <p>Balance: ${{data.balance}}</p>

        <h2>Change e-mail</h2>
        <form action="{{url_for('change_email')}}" method="post">
            <input type="email" name="email" required>
            <button>Update</button>
        </form>
        <p><a href="{{url_for('logout')}}">Log out</a></p>
    """, user=session["user"], data=user)

@app.route("/login", methods=["GET", "POST"])
def login():
    if request.method == "POST":
        user = request.form.get("user")
        if user in USERS:
            session["user"] = user
            return redirect(url_for("index"))
        abort(403)
    return """
        <h1>Log in as Alice</h1>
        <form method="post">
            <input type="hidden" name="user" value="alice">
            <button>Log in</button>
        </form>
    """

@app.route("/logout")
def logout():
    session.clear()
    return redirect(url_for("login"))

@app.route("/change-email", methods=["POST"])
def change_email():
    user = current_user()
    if not user:
        abort(403)
    new_email = request.form.get("email", "")
    user["email"] = new_email
    return f"Email changed to {new_email}. <a href='/'>Back</a>"

# ── run ──────────────────────────────────────────────────────────────────────────
if __name__ == "__main__":
    app.run(debug=True)


```
