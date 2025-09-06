from flask import Flask, render_template, jsonify
import os

app = Flask(__name__)

DATA_FILE = "stats.txt"

def read_stats():
    if not os.path.exists(DATA_FILE):
        return 0, 0
    try:
        with open(DATA_FILE, "r") as f:
            d = f.read().split(",")
            return int(d[0]), int(d[1])
    except:
        return 0, 0

@app.route("/")
def index():
    return render_template("index.html")

@app.route("/api/stats")
def api_stats():
    win, lose = read_stats()
    total = win + lose
    win_rate = (win / total * 100) if total > 0 else 0
    return jsonify({
        "win": win,
        "lose": lose,
        "total": total,
        "win_rate": round(win_rate,2)
    })

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=8080)
