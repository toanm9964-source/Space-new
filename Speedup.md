{
  "RealTimeGameSystem": {
    "TickIntervalSeconds": 1,

    "ProgressTypes": [
      "build",
      "research",
      "ship_construction",
      "repair"
    ],

    "SpeedUpItems": {
      "Types": [
        "BuildSpeedUp",
        "ResearchSpeedUp",
        "RepairSpeedUp",
        "UniversalSpeedUp"
      ],
      "Durations": [
        { "id": "1m", "seconds": 60 },
        { "id": "5m", "seconds": 300 },
        { "id": "15m", "seconds": 900 },
        { "id": "1h", "seconds": 3600 },
        { "id": "3h", "seconds": 10800 },
        { "id": "8h", "seconds": 28800 },
        { "id": "1d", "seconds": 86400 },
        { "id": "5d", "seconds": 432000 },
        { "id": "10d", "seconds": 864000 }
      ]
    },

    "ProgressObjectTemplate": {
      "id": "",
      "type": "",
      "timeTotal": 0,
      "timeRemaining": 0,
      "isFinished": false
    },

    "Logic": {
      "TimeUpdate": {
        "formula": "timeRemaining = max(0, timeRemaining - TickIntervalSeconds)",
        "onFinish": "if timeRemaining <= 0 → isFinished = true"
      },

      "SpeedUpApplication": {
        "Validation": {
          "BuildSpeedUp": "Allowed only when type == 'build'",
          "ResearchSpeedUp": "Allowed only when type == 'research'",
          "RepairSpeedUp": "Allowed only when type == 'repair'",
          "UniversalSpeedUp": "Allowed for all types"
        },
        "Formula": "timeRemaining = max(0, timeRemaining - speedUp.seconds)",
        "AutoFinishCheck": "if timeRemaining == 0 → isFinished = true"
      }
    }
  }
}
