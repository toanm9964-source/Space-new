{
  "CommandersSystem": {
    "MaxFleetSlotsPerCommander": 5,

    "CommanderLevelConfig": {
      "MaxLevel": 50,
      "ExpCurveFormula": "expRequired = level * level * 120",
      "ExpGainPerBattle": {
        "Small": 50,
        "Medium": 120,
        "Large": 250,
        "Boss": 600
      }
    },

    "CommanderTypes": {
      "NormalCommanders": [
        {
          "id": "CMD_Strategist",
          "rarity": "Normal",
          "role": "Fleet Tactician",
          "baseBuffs": {
            "damagePercent": 5,
            "evasionPercent": 3,
            "hpPercent": 4
          },
          "skills": [
            {
              "name": "Tactical Insight",
              "levelScaling": "damagePercent +0.3% mỗi level",
              "maxEffect": 20
            }
          ]
        },
        {
          "id": "CMD_Guardian",
          "rarity": "Normal",
          "role": "Defense Specialist",
          "baseBuffs": {
            "shieldPercent": 7,
            "armorPercent": 5,
            "hpPercent": 3
          },
          "skills": [
            {
              "name": "Defensive Matrix",
              "levelScaling": "armorPercent +0.5% mỗi level",
              "maxEffect": 30
            }
          ]
        },
        {
          "id": "CMD_Engineer",
          "rarity": "Normal",
          "role": "Repair Specialist",
          "baseBuffs": {
            "repairSpeedPercent": 10,
            "maintenanceCostReduction": 5
          },
          "skills": [
            {
              "name": "Auto-Repair Protocol",
              "levelScaling": "repairSpeedPercent +1% mỗi level",
              "maxEffect": 40
            }
          ]
        }
      ],

      "EliteCommanders": [
        {
          "id": "CMD_AdmiralNova",
          "rarity": "Elite",
          "role": "Aggressive Fleet Commander",
          "baseBuffs": {
            "damagePercent": 12,
            "weaponSpeedPercent": 8,
            "criticalChancePercent": 5
          },
          "skills": [
            {
              "name": "Overcharge",
              "effect": "Tăng sát thương toàn hạm đội",
              "levelScaling": "damagePercent +1.2% mỗi level",
              "maxEffect": 60
            },
            {
              "name": "Precision Strike",
              "effect": "Tăng sát thương vào tàu lớn (BattleShip, Titan)",
              "bonus": 15,
              "scaling": "+0.6% mỗi level"
            }
          ]
        },
        {
          "id": "CMD_EternalShield",
          "rarity": "Elite",
          "role": "Ultimate Tank Commander",
          "baseBuffs": {
            "hpPercent": 15,
            "shieldPercent": 12,
            "armorPercent": 10,
            "evasionPercent": 5
          },
          "skills": [
            {
              "name": "Absolute Barrier",
              "effect": "Tăng khiêng 20% cơ bản",
              "levelScaling": "+1% mỗi level",
              "maxEffect": 70
            },
            {
              "name": "Fortress Mode",
              "effect": "Giảm sát thương nhận vào toàn hạm đội",
              "percent": 10,
              "scaling": "+0.4% mỗi level"
            }
          ]
        }
      ]
    },

    "FleetSynergyRules": {
      "ShipTypeBonuses": [
        {
          "type": "SmallShip",
          "bonus": {
            "evasionPercent": 5,
            "weaponSpeedPercent": 3
          }
        },
        {
          "type": "MediumShip",
          "bonus": {
            "hpPercent": 4,
            "damagePercent": 2
          }
        },
        {
          "type": "HeavyShip",
          "bonus": {
            "armorPercent": 6,
            "hpPercent": 8
          }
        },
        {
          "type": "BattleShip",
          "bonus": {
            "damagePercent": 10,
            "shieldPercent": 5
          }
        },
        {
          "type": "Titan",
          "bonus": {
            "hpPercent": 20,
            "armorPercent": 15,
            "damagePercent": 12
          }
        }
      ],

      "WeaponSynergyBonuses": [
        {
          "weapon": "Cannon",
          "bonus": { "damagePercent": 5 }
        },
        {
          "weapon": "Laser",
          "bonus": { "shieldPenetrationPercent": 8 }
        },
        {
          "weapon": "Missile",
          "bonus": { "criticalChancePercent": 6 }
        },
        {
          "weapon": "Drone",
          "bonus": { "evasionPercent": 7 }
        }
      ]
    },

    "FinalBuffFormula": {
      "formula": "FinalStats = BaseStats * (1 + CommanderBuff + ShipSynergyBuff + WeaponSynergyBuff + ResearchBuff + AllianceBuff)"
    }
  }
}
