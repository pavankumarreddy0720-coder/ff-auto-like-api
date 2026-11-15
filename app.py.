
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route("/", methods=["GET"])
def home():
    return jsonify({
        "status": "online",
        "name": "FF AUTO LIKE API",
        "region": "IND"
    })

@app.route("/like", methods=["POST"])
def like():
    data = request.get_json(silent=True) or {}

    uid = str(data.get("uid", "")).strip()
    region = str(data.get("region", "")).lower()

    if region != "ind":
        return jsonify({
            "success": False,
            "message": "Only India region is supported"
        }), 400

    if not uid.isdigit() or not 5 <= len(uid) <= 20:
        return jsonify({
            "success": False,
            "message": "Invalid Free Fire UID"
        }), 400

    return jsonify({
        "success": True,
        "message": "UID validated. No likes have been sent.",
        "uid": uid,
        "region": "IND"
    })

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=10000)
