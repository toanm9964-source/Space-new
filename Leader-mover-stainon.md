=== FLEET MOVEMENT SYSTEM ===
FLEET_MOVEMENT:
  base_speed:
    small_ship: 150
    light_ship: 120
    medium_ship: 90
    battleship: 70
    dreadnought: 50
    supernova_ship: 40

  travel_formula: "travel_time = distance / fleet_speed"
  fleet_speed_rule: "fleet_speed = speed_of_slowest_ship"

  warp_charge_time: 3.0
  warp_cooldown: 1.5
  warp_speed_multiplier: 2.5



=== LEADERS (ADMIRALS) ===
NORMAL_LEADERS:

  - name: "Arin Valos"
    type: tactical
    bonus:
      accuracy: +5%
      evasion: +3%
      speed: +10%

  - name: "Lira Solen"
    type: engineer
    bonus:
      armor: +7%
      shield: +5%
      repair_rate: +15%

  - name: "Darin Kroll"
    type: strategist
    bonus:
      damage: +6%
      fleet_size_limit: +10
      retreat_speed: +15%

POWER_LEADERS:

  - name: "Valkar The Red Sun"
    type: legendary_offense
    bonus:
      damage: +20%
      crit_chance: +10%
      missile_penetration: +15%
      special: "Radiation Burn: Enemy receives 2% max HP burn per second for 5 sec"

  - name: "Serena Voidcaller"
    type: legendary_defense
    bonus:
      shield: +25%
      shield_regen: +40%
      armor: +20%
      special: "Void Barrier: First hit every 10 sec is reduced by 80%"



=== STATION UPGRADES ===
STATION_LEVELS:
  level_1:
    build_speed: 1.0
    research_speed: 1.0
    shipyard_speed: 1.0
    max_fleet: 1

  level_2:
    build_speed: 1.1
    research_speed: 1.05
    shipyard_speed: 1.1
    max_fleet: 2

  level_3:
    build_speed: 1.25
    research_speed: 1.15
    shipyard_speed: 1.25
    max_fleet: 3

  level_4:
    build_speed: 1.40
    research_speed: 1.25
    shipyard_speed: 1.40
    max_fleet: 4

  level_5:
    build_speed: 1.60
    research_speed: 1.40
    shipyard_speed: 1.60
    max_fleet: 5



=== RESEARCH SYSTEM ===
RESEARCH_TREE:

  ECONOMY:
    - name: "Fast Construction"
      effect: "Station build speed +10%"
    - name: "Advanced Fabrication"
      effect: "Station build speed +20%"

    - name: "Rapid Ship Production"
      effect: "Shipyard build speed +15%"
    - name: "Fleet Fabrication Matrix"
      effect: "Shipyard build speed +30%"

    - name: "Efficient Research Algorithms"
      effect: "Research speed +10%"
    - name: "Quantum Research Core"
      effect: "Research speed +25%"


  MILITARY:
    - name: "Reinforced Hull"
      effect: "All ships +10% HP"
    - name: "Titan Alloy Plating"
      effect: "All ships +20% HP"

    - name: "Weapon Optimization"
      effect: "+8% ship damage"
    - name: "Quantum Firepower"
      effect: "+15% ship damage"

    - name: "Fleet Logistics"
      effect: "-10% fleet maintenance"
    - name: "Voidline Supply System"
      effect: "-20% fleet maintenance"


  SPECIAL:
    - name: "Shield Resonance"
      effect: "+15% shield"
    - name: "Overcharge Capacitors"
      effect: "+20% laser damage"

    - name: "Missile Target AI"
      effect: "+20% missile accuracy"
    - name: "Drone Swarm Matrix"
      effect: "+25% drone count"

    - name: "Instant Warp"
      effect: "Warp charge time -50%"
    - name: "Subspace Echo Maneuvering"
      effect: "Evasion +10%"
