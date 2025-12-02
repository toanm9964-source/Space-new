=== RESOURCE SYSTEM ===

RESOURCES:
  metal: "Dùng xây tàu và trạm, giáp và thân tàu"
  gas: "Dùng để xây khiên, động cơ, laser"
  energy: "Bảo trì trạm và đội tàu, chạy warp"
  crystal: "Dùng cho công nghệ laser, máy tính tàu"
  exotic: "Dùng cho tàu cao cấp và công nghệ cực hiếm"
  nanite: "Dùng để sửa chữa nhanh và giảm thời gian xây dựng"

=== BUILD COST ===

STATION_BUILD_COST:
  outpost:
    metal: 300
    gas: 100
    energy: 50
  defense_station:
    metal: 600
    gas: 200
    crystal: 100
  starfortress:
    metal: 1200
    gas: 500
    crystal: 300
    exotic: 5

SHIP_BUILD_COST:
  small_ship:
    metal: 80
    gas: 20
    energy: 10
  light_ship:
    metal: 120
    gas: 40
    energy: 20
  medium_ship:
    metal: 220
    gas: 60
    crystal: 20
    energy: 30
  battleship:
    metal: 500
    gas: 150
    crystal: 60
    energy: 80
  dreadnought:
    metal: 800
    gas: 300
    crystal: 120
    exotic: 3
    energy: 100
  supernova_ship:
    metal: 1500
    gas: 700
    crystal: 300
    exotic: 10
    nanite: 50
    energy: 150

=== MAINTENANCE ===

FLEET_MAINTENANCE:
  small_ship: { energy: 1 }
  light_ship: { energy: 2 }
  medium_ship: { energy: 3 }
  battleship: { energy: 6 }
  dreadnought: { energy: 12 }
  supernova_ship: { energy: 20 }

STATION_MAINTENANCE:
  outpost: { energy: 5 }
  defense_station: { energy: 12 }
  starfortress: { energy: 20 }

=== SHIP REPAIR COST ===

REPAIR_COST:
  per_1_percent_hp:
    metal: 1
    gas: 0.5
    nanite: 0.1

repair_supernova:
  per_1_percent_hp:
    metal: 3
    gas: 2
    nanite: 2
    exotic: 0.05

=== RESOURCE DROPS FROM DESTROYED SHIPS ===

DESTROY_REWARD:
  small_ship:
    metal: 10
    gas: 5
  light_ship:
    metal: 20
    gas: 8
  medium_ship:
    metal: 40
    gas: 20
    crystal: 5
  battleship:
    metal: 90
    gas: 40
    crystal: 15
  dreadnought:
    metal: 150
    gas: 80
    crystal: 30
    exotic: 1
  supernova_ship:
    metal: 300
    gas: 150
    crystal: 80
    exotic: 3
    nanite: 5

DROP_RATE:
  metal: "100% rơi"
  gas: "95% rơi"
  crystal: "70% rơi (nếu tàu có crystal)"
  exotic: "40% rơi từ tàu cấp cao"
  nanite: "50% rơi từ tàu cấp cao"

=== ALLIANCE SYSTEM ===

ALLIANCE_TYPES:

  pact:
    name: "Hiệp Ước"
    effect:
      trade_bonus: "+10% thương mại"
      diplomacy: "+20 điểm quan hệ"

  defense_alliance:
    name: "Liên Minh Phòng Thủ"
    effect:
      hp_bonus: "+5% HP toàn bộ tàu"
      fleet_speed: "+10% tốc độ di chuyển"

  full_alliance:
    name: "Liên Minh Toàn Diện"
    effect:
      damage_bonus: "+10% sát thương"
      economy_bonus: "+10% tài nguyên"
      research_speed: "+10% tốc độ nghiên cứu"

  federation:
    name: "Liên Bang Galatic"
    effect:
      shared_tech_speed: "+20% nghiên cứu chia sẻ"
      navy_capacity: "+15% giới hạn hạm đội"
      special_fleet: "Hạm đội Liên Bang – mạnh nhất game"
      unity_bonus: "+10% giảm bảo trì tàu"
