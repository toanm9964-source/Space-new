{
  "meta": {
    "project": "Space Strategy - Config Full Pack",
    "author": "you (replace assets/names as desired)",
    "note": "Avoid using Nova Empire assets / names. Use original art, icons and text."
  },

  "ui_flow": {
    "screens": [
      {"id":"main_menu","title":"Main Menu","elements":["Play","Campaign","Multiplayer","Settings","Profile"]},
      {"id":"galaxy_view","title":"Galaxy","elements":["Map","FleetsPanel","SelectedStationPanel","MoveButton","Zoom"]},
      {"id":"station_view","title":"Station","elements":["StationStats","Modules","BuildQueue","RepairQueue","ResearchQueue","UpgradeButton"]},
      {"id":"fleet_view","title":"Fleet","elements":["FleetList","FleetStats","FormationSelect","MoveQueue","AssignCommander"]},
      {"id":"battle_view","title":"Battle","elements":["BattleLog","FormationPanel","AbilityPanel","Pause","Speed"]},
      {"id":"research_view","title":"Research","elements":["Tree","ActiveResearch","UseSpeedup"]},
      {"id":"commander_view","title":"Commander","elements":["CommanderList","LevelUp","AssignShips","Skills"]},
      {"id":"alliance_view","title":"Alliance","elements":["Members","Donations","AllianceResearch","AllianceBuffs"]},
      {"id":"inventory_view","title":"Inventory","elements":["Speedups","Materials","Consumables","UseItem"]}
    ],
    "flow_rules": [
      {"from":"main_menu","to":"galaxy_view"},
      {"from":"galaxy_view","to":"station_view","condition":"select_station"},
      {"from":"galaxy_view","to":"fleet_view","condition":"select_fleet"},
      {"from":"station_view","to":"research_view","condition":"press_research"},
      {"from":"fleet_view","to":"battle_view","condition":"engage_enemy"}
    ]
  },

  "fleet_movement": {
    "movement_rules": {
      "fleet_speed": "min(ship.speed over fleet)",
      "travel_time_formula": "time = distance / fleet_speed", 
      "fuel_consumption_per_km": 0.01,
      "warp_mode": {"enabled":true,"charge_seconds":3,"cooldown_seconds":10,"warp_multiplier":2.5},
      "arrival_behavior": ["attack_if_hostile","dock_if_friend","wait_at_location"]
    },
    "queue": {
      "max_orders_per_fleet": 5,
      "order_types":["move","attack","dock","patrol","return"]
    },
    "fuel": {
      "resource":"gas",
      "refuel_rules":"refuel_at_station_or_resource_nodes",
      "low_fuel_threshold_percent":0.15
    }
  },

  "battle_engine": {
    "tick_interval_seconds": 0.2,
    "target_selection": {
      "priority": ["capital_ships","highest_dps","lowest_hp","nearest"],
      "focus_fire_window_seconds": 5,
      "assign_rule": "allocate ships until estimated kill within focus_fire_window or until no more ships"
    },
    "formations": {
      "line":"maximize frontal firepower",
      "wedge":"pierce through shields",
      "spread":"reduce AoE hit",
      "escort":"protect capital ship",
      "skirmish":"kite fast ships"
    },
    "combat_flow": [
      "1. evaluate threats and choose formation",
      "2. assign targets using priority weights",
      "3. each ship performs aim & fire with accuracy check",
      "4. apply shield absorption, armor reduction, criticals",
      "5. update hp/shield, check deaths, spawn salvage",
      "6. check retreat/reinforce conditions"
    ],
    "damage_formula": {
      "base_damage":"weapon.damage",
      "hit_check":"rand <= (weapon.accuracy * (1 - target.evasion)) or if weapon.type == 'missile' then ignore evasion",
      "shield_rule":"apply damage to shield first; shields can regen out-of-combat",
      "armor_rule":"damage_after_armor = base_damage * (1 - target.armor/400) // clamp 0.05..0.6",
      "critical":"if rand < crit_chance then damage *= 1.5",
      "class_multiplier":"apply ship type multiplier based on weapon vs ship class"
    },
    "support_actions": {
      "repair_drones":"use if fleet_avg_hp < repair_threshold and repair_bay_available",
      "shield_overcharge":"use when predicted incoming_damage_next_3s > shield_current",
      "emp":"use on groups with many drones or high accuracy"
    },
    "salvage": {
      "drop_rules":"on_ship_destroyed spawn salvage according to DESTROY_REWARD table",
      "loot_claim":"player must send salvage fleet or have station nearby to auto-collect"
    }
  },

  "missions_and_achievements": {
    "mission_types":["tutorial","daily","weekly","story","side"],
    "mission_example": [
      {"id":"m_tutorial_1","title":"Build Outpost","type":"tutorial","objective":"Build an Outpost","reward":{"metal":200,"speedup":"su_5m"}},
      {"id":"m_daily_1","title":"Collect resources","type":"daily","objective":"Collect 500 metal in a day","reward":{"crystal":5,"exp":100}}
    ],
    "achievement_example":[
      {"id":"ach_first_battle","title":"First Blood","desc":"Win first battle","reward":{"speedup":"su_15m","commander_exp":50}}
    ],
    "tracking":"store mission progress in save system; daily reset at server-time or local-day with monotonic check"
  },

  "stations": {
    "modules": {
      "shipyard":{"effect":"+build_slots","base_cost":{"metal":300,"gas":80},"build_time":3600},
      "advanced_shipyard":{"effect":"+2 build_slots,+15% build speed","requires":["tech.nanos"],"base_cost":{"metal":700,"gas":150,"crystal":50},"build_time":7200},
      "radar":{"effect":"+20% vision","base_cost":{"metal":150,"gas":50},"build_time":900},
      "sensor_array":{"effect":"+40% detection","requires":["tech.quantum"],"base_cost":{"metal":300,"gas":100,"crystal":30},"build_time":1800},
      "power_core":{"effect":"+energy_capacity","base_cost":{"metal":200,"gas":100},"build_time":1200},
      "repair_bay":{"effect":"+repair_speed","base_cost":{"metal":350,"gas":120,"nanite":10},"build_time":1800},
      "warehouse":{"effect":"+storage","base_cost":{"metal":400},"build_time":600},
      "research_lab":{"effect":"+research_speed","base_cost":{"metal":300,"gas":80,"crystal":20},"build_time":1500}
    },
    "upgrade_requirements": {
      "station_level_2":{"requires_tech":["construction_basic"],"cost":{"metal":600,"gas":200,"crystal":100},"time":7200},
      "station_level_3":{"requires_tech":["construction_ai"],"cost":{"metal":1500,"gas":600,"crystal":300,"exotic":5},"time":14400},
      "station_level_4":{"requires_tech":["nano_fabrication"],"cost":{"metal":3000,"gas":1200,"crystal":500,"exotic":15,"nanite":20},"time":28800}
    },
    "maintenance_per_hour": {"outpost":5,"defense_station":12,"starfortress":20}
  },

  "resources": {
    "basic":["metal","gas","energy","crystal"],
    "advanced":["exotic","nanite","crew"],
    "production": {
      "mine":{"produces":{"metal":10},"workers_required":0},
      "gas_harvester":{"produces":{"gas":6},"workers_required":0},
      "solar_array":{"produces":{"energy":8},"workers_required":0},
      "crystal_field":{"produces":{"crystal":2},"workers_required":0}
    },
    "storage_caps": {"starter":1000,"warehouse_level1":2000,"warehouse_level2":5000}
  },

  "alliance_system": {
    "roles":["leader","officer","member"],
    "donation": {
      "allowed_resources":["metal","gas","crystal","exotic","nanite"],
      "donation_rewards":{"alliance_score":1,"alliance_funds":100}
    },
    "alliance_research": {
      "shared_bonuses":["fleet_capacity","research_speed","economy_bonus"],
      "example":{"name":"Shared Logistics","effect":"+10% alliance fleet_capacity","cost":{"crystal":500,"exotic":2},"time":86400}
    },
    "alliance_buildings": {"alliance_hangar":{"effect":"shared_shipyard","+cost":5000}}
  },

  "events_system": {
    "event_types":["random","timed","boss","seasonal"],
    "random_event_example":{"id":"pirate_raid","trigger":"enter_system_without_outpost","effect":"spawn_pirate_raiders","reward":"loot"},
    "timed_event_example":{"id":"research_double","schedule":"weekly","effect":"research_speed +100% for 4h"},
    "boss_event_example":{"id":"ancient_dreadnought","spawn_condition":"world_level>=10","reward":"high_exotic_and_rare_modules"}
  },

  "production_system": {
    "generation_formula":"production_per_hour * (1 + station_bonus + alliance_bonus) - maintenance",
    "auto_collection":"if player_station_has_warehouse then auto_collect else must send freighter",
    "consumption":"ships consume energy per hour; if not enough energy -> reduced performance"
  },

  "save_system": {
    "method":"local_save_json",
    "autosave_interval_seconds":10,
    "anti_clock_cheat":"use_monotonic_time_for_elapsed_calculation",
    "save_fields":["player_resources","fleets","stations","research","missions","inventory","last_monotonic_time"],
    "monotonic_example":"store last_monotonic = SystemClock.elapsedRealtime() (or equivalent). On load: delta = now - last_monotonic; apply delta to countdowns"
  },

  "speedups": {
    "types":["BuildSpeedUp","ResearchSpeedUp","RepairSpeedUp","UniversalSpeedUp"],
    "durations_seconds":[60,300,900,3600,10800,28800,86400,432000,864000],
    "rules": {
      "apply":"timeRemaining = max(0,timeRemaining - seconds)",
      "stacking":"additive_time",
      "max_active_cap_seconds":604800
    }
  },

  "battle_sim_examples": {
    "sample_weapon": {"name":"Light Cannon","damage":20,"accuracy":0.75,"rof":1.5,"type":"cannon"},
    "sample_ship": {"class":"small","hp":80,"shield":60,"armor":20,"evasion":0.2},
    "simulate_step_pseudocode":"for each ship: if rand<=accuracy*(1-evasion) then baseDamage=weapon.damage; apply shield; apply armor reduction; apply crit; update hp"
  },

  "commander_and_exp": {
    "exp_curve":"expRequired = level * level * 120",
    "exp_sources":{"battle_win":200,"mission_complete":100},
    "commander_slot_per_player":5,
    "commander_assign_rules":"one commander per fleet; commander buffs applied to assigned fleet"
  },

  "dev_notes": {
    "copyright_guidelines":"Do not copy names, art, music, text from existing commercial games (e.g., Nova Empire). Use original names, procedurally-generated art or royalty-free assets. For inspiration it's fine, but avoid direct copying.",
    "next_steps":"Implement UI using screens defined; wire ProgressObjects to save_system; implement battle tick using battle_engine.tick_interval_seconds"
  }
}
