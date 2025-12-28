# Reduce-your-screen-time-detox-system
Design your own digital 
import React, { useState, useEffect } from "react";
import { LineChart, Line, XAxis, YAxis, Tooltip } from "recharts";

export default function App() {
  const [todayUsage, setTodayUsage] = useState(5);
  const [target, setTarget] = useState(3);
  const [history, setHistory] = useState([]);
  const [streak, setStreak] = useState(0);
  const [xp, setXp] = useState(0);

  useEffect(() => {
    const saved = JSON.parse(localStorage.getItem("history")) || [];
    setHistory(saved);
  }, []);

  const saveToday = () => {
    const newEntry = {
      day: `Day ${history.length + 1}`,
      usage: todayUsage,
    };

    const newHistory = [...history, newEntry];
    setHistory(newHistory);
    localStorage.setItem("history", JSON.stringify(newHistory));

    if (todayUsage <= target) {
      setStreak(streak + 1);
      setXp(xp + 50);
    } else {
      setStreak(0);
    }
  };

  return (
    <div style={{ padding: 20, fontFamily: "Arial" }}>
      <h1>🔥 FocusForge Dashboard</h1>

      <h3>📊 Baseline & Target</h3>
      <label>Today's Screen Time (hrs): </label>
      <input
        type="number"
        value={todayUsage}
        onChange={(e) => setTodayUsage(Number(e.target.value))}
      />
      <br />

      <label>Target (hrs): </label>
      <input
        type="number"
        value={target}
        onChange={(e) => setTarget(Number(e.target.value))}
      />
      <br /><br />

      <button onClick={saveToday}>Save Today</button>

      <h3>🔥 Streak: {streak} days</h3>
      <h3>🏆 XP: {xp}</h3>

      <h3>📈 Progress Tracker</h3>
      <LineChart width={300} height={200} data={history}>
        <XAxis dataKey="day" />
        <YAxis />
        <Tooltip />
        <Line type="monotone" dataKey="usage" strokeWidth={2} />
      </LineChart>

      <h3>🎯 Focus Session</h3>
      <p>Start a 25-minute distraction-free session</p>
      <button onClick={() => alert("Focus Session Started 🔕")}>
        Start Focus
      </button>

      <h3>🤝 Peer Accountability (Mock)</h3>
      <p>You & Rahul both hit targets today 🎉</p>
    </div>
  );
}
import React, { useState, useEffect } from "react";
import { LineChart, Line, XAxis, YAxis, Tooltip } from "recharts";

export default function App() {
  const [todayUsage, setTodayUsage] = useState(5);
  const [target, setTarget] = useState(3);
  const [history, setHistory] = useState([]);
  const [streak, setStreak] = useState(0);
  const [xp, setXp] = useState(0);

  useEffect(() => {
    const saved = JSON.parse(localStorage.getItem("history")) || [];
    setHistory(saved);
  }, []);

  const saveToday = () => {
    const newEntry = {
      day: `Day ${history.length + 1}`,
      usage: todayUsage,
    };

    const newHistory = [...history, newEntry];
    setHistory(newHistory);
    localStorage.setItem("history", JSON.stringify(newHistory));

    if (todayUsage <= target) {
      setStreak(streak + 1);
      setXp(xp + 50);
    } else {
      setStreak(0);
    }
  };

  return (
    <div style={{ padding: 20, fontFamily: "Arial" }}>
      <h1>🔥 FocusForge Dashboard</h1>

      <h3>📊 Baseline & Target</h3>
      <label>Today's Screen Time (hrs): </label>
      <input
        type="number"
        value={todayUsage}
        onChange={(e) => setTodayUsage(Number(e.target.value))}
      />
      <br />

      <label>Target (hrs): </label>
      <input
        type="number"
        value={target}
        onChange={(e) => setTarget(Number(e.target.value))}
      />
      <br /><br />

      <button onClick={saveToday}>Save Today</button>

      <h3>🔥 Streak: {streak} days</h3>
      <h3>🏆 XP: {xp}</h3>

      <h3>📈 Progress Tracker</h3>
      <LineChart width={300} height={200} data={history}>
        <XAxis dataKey="day" />
        <YAxis />
        <Tooltip />
        <Line type="monotone" dataKey="usage" strokeWidth={2} />
      </LineChart>

      <h3>🎯 Focus Session</h3>
      <p>Start a 25-minute distraction-free session</p>
      <button onClick={() => alert("Focus Session Started 🔕")}>
        Start Focus
      </button>

      <h3>🤝 Peer Accountability (Mock)</h3>
      <p>You & Rahul both hit targets today 🎉</p>
    </div>
  );
}
