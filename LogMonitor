import { useState } from "react";
import React from "react";

const suspiciousPatterns = [
  /failed login/i,
  /unauthorized access/i,
  /malicious activity detected/i,
];

export default function LogMonitor() {
  const [logs, setLogs] = useState("");
  const [alerts, setAlerts] = useState([]);

  const handleLogInput = (event) => {
    const newLogs = event.target.value;
    setLogs(newLogs);
    checkForAlerts(newLogs);
  };

  const checkForAlerts = (logData) => {
    const logLines = logData.split("\n");
    const newAlerts = logLines.filter((line) =>
      suspiciousPatterns.some((pattern) => pattern.test(line))
    );
    setAlerts(newAlerts);
  };

  return (
    <div className="p-4 bg-gray-900 text-white min-h-screen">
      <h1 className="text-2xl font-bold mb-4">Log Monitoring System</h1>
      <textarea
        className="w-full h-48 p-2 bg-gray-800 text-white border border-gray-600 rounded"
        placeholder="Paste log data here..."
        value={logs}
        onChange={handleLogInput}
      ></textarea>
      <div className="mt-4">
        <h2 className="text-xl font-semibold">Alerts</h2>
        <ul className="mt-2">
          {alerts.length > 0 ? (
            alerts.map((alert, index) => (
              <li key={index} className="bg-red-600 p-2 mt-1 rounded">
                ⚠️ Alert: {alert}
              </li>
            ))
          ) : (
            <li className="text-green-400">No suspicious activity detected.</li>
          )}
        </ul>
      </div>
    </div>
  );
}
