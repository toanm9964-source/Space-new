{
  "weapons": {
    "cannon": [
      { "name": "Light Cannon", "damage": 20, "fire_rate": 1.5, "range": 300, "accuracy": 0.75, "bonus_vs_armor": 0.30 },
      { "name": "Medium Cannon", "damage": 40, "fire_rate": 2.5, "range": 350, "accuracy": 0.70, "bonus_vs_armor": 0.30 },
      { "name": "Heavy Cannon", "damage": 80, "fire_rate": 3.5, "range": 400, "accuracy": 0.60, "bonus_vs_armor": 0.30 }
    ],
    "laser": [
      { "name": "Laser Beam", "damage": 15, "fire_rate": 1.2, "range": 350, "accuracy": 0.90, "bonus_vs_shield": 0.40 },
      { "name": "Pulse Laser", "damage": 30, "fire_rate": 2.0, "range": 380, "accuracy": 0.85, "bonus_vs_shield": 0.40 },
      { "name": "Heavy Laser", "damage": 60, "fire_rate": 3.0, "range": 420, "accuracy": 0.80, "bonus_vs_shield": 0.40 }
    ],
    "missiler": [
      { "name": "Light Missile", "damage": 35, "fire_rate": 2.0, "range": 500, "accuracy": 0.85, "ignore_dodge": true },
      { "name": "Heavy Missile", "damage": 70, "fire_rate": 3.0, "range": 550, "accuracy": 0.80, "ignore_dodge": true },
      { "name": "Nuclear Missile", "damage": 150, "fire_rate": 6.0, "range": 600, "accuracy": 0.75, "ignore_dodge": true }
    ],
    "drone": [
      { "name": "Light Drone", "damage": 8, "fire_rate": 0.8, "range": 250, "accuracy": 0.85, "bonus_vs_small": 0.10 },
      { "name": "Combat Drone", "damage": 15, "fire_rate": 1.0, "range": 280, "accuracy": 0.90, "bonus_vs_small": 0.10 },
      { "name": "Assault Drone", "damage": 25, "fire_rate": 1.2, "range": 320, "accuracy": 0.88, "bonus_vs_small": 0.10 }
    ]
  },

  "materials": {
    "armor": { "base_value": 40, "physical_reduction": 0.20 },
    "shield": { "base_value": 60, "energy_reduction": 0.25 },
    "hp": { "base_value": 100 },
    "dodge": { "base_value": 0.05, "max_value": 0.30 }
  },

  "ships": [
    {
      "name": "Small Ship",
      "hp": 120,
      "armor": 20,
      "shield": 40,
      "dodge": 0.15,
      "speed": 150,
      "weapon_slots": 1
    },
    {
      "name": "Light Ship",
      "hp": 200,
      "armor": 35,
      "shield": 60,
      "dodge": 0.10,
      "speed": 120,
      "weapon_slots": 2
    },
    {
      "name": "Medium Ship",
      "hp": 350,
      "armor": 50,
      "shield": 90,
      "dodge": 0.06,
      "speed": 90,
      "weapon_slots": 3
    },
    {
      "name": "Battleship",
      "hp": 600,
      "armor": 80,
      "shield": 120,
      "dodge": 0.03,
      "speed": 70,
      "weapon_slots": 4
    },
    {
      "name": "Dreadnought",
      "hp": 900,
      "armor": 120,
      "shield": 180,
      "dodge": 0.02,
      "speed": 50,
      "weapon_slots": 5
    },
    {
      "name": "Supernova Ship",
      "hp": 1500,
      "armor": 180,
      "shield": 250,
      "dodge": 0.01,
      "speed": 40,
      "weapon_slots": 6,
      "special": "radiation_damage_aura"
    }
  ]
}
