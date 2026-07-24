from flask import Flask, request, jsonify

app = Flask(__name__)

messages = []

@app.route("/")
def home():
    return "🤖 هرمز سرور روشن است"

@app.route("/send", methods=["POST"])
def send():
    data = request.json
    messages.append(data)
    return jsonify({"status": "ok"})

@app.route("/messages")
def get_messages():
    return jsonify(messages)

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=10000)
