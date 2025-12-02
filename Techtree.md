=== TECH TREE ===

TECH_TREE:

  construction_speed:
    tier_1:
      name: "Cơ Khí Cơ Bản"
      effect: "Tăng tốc xây trạm +10%"
      cost: 200 research
    tier_2:
      name: "Tự Động Hóa Công Trường"
      effect: "Tăng tốc xây trạm +20%"
      cost: 500 research
      requires: ["Cơ Khí Cơ Bản"]
    tier_3:
      name: "AI Điều Hành Xây Dựng"
      effect: "Tăng tốc xây trạm +35%"
      cost: 1200 research
      requires: ["Tự Động Hóa Công Trường"]

  research_speed:
    tier_1:
      name: "Tối Ưu Hóa Phòng Thí Nghiệm"
      effect: "Tốc độ nghiên cứu +10%"
      cost: 200 research
    tier_2:
      name: "Máy Tính Lượng Tử"
      effect: "Tốc độ nghiên cứu +20%"
      cost: 600 research
      requires: ["Tối Ưu Hóa Phòng Thí Nghiệm"]
    tier_3:
      name: "AI Tự Lập Luận"
      effect: "Tốc độ nghiên cứu +30%"
      cost: 1500 research
      requires: ["Máy Tính Lượng Tử"]

  shipyard_speed:
    tier_1:
      name: "Hợp Kim Nhẹ"
      effect: "Tốc độ đóng tàu +10%"
      cost: 150 research
    tier_2:
      name: "Tự Động Hóa Xưởng Đóng"
      effect: "Tốc độ đóng tàu +25%"
      cost: 450 research
      requires: ["Hợp Kim Nhẹ"]
    tier_3:
      name: "Nano Lắp Ghép"
      effect: "Tốc độ đóng tàu +40%"
      cost: 1300 research
      requires: ["Tự Động Hóa Xưởng Đóng"]

  fleet_damage:
    tier_1:
      name: "Cơ Khí Vũ Khí"
      effect: "Sát thương hạm đội +5%"
      cost: 250 research
    tier_2:
      name: "Hệ Thống Ổn Định Năng Lượng"
      effect: "Sát thương hạm đội +12%"
      cost: 800 research
      requires: ["Cơ Khí Vũ Khí"]
    tier_3:
      name: "Chiến Thuật Tác Chiến AI"
      effect: "Sát thương hạm đội +20%"
      cost: 2000 research
      requires: ["Hệ Thống Ổn Định Năng Lượng"]

  fleet_hp:
    tier_1:
      name: "Cường Hóa Hợp Kim"
      effect: "Máu tàu +5%"
      cost: 250 research
    tier_2:
      name: "Vật Liệu Siêu Bền"
      effect: "Máu tàu +12%"
      cost: 700 research
      requires: ["Cường Hóa Hợp Kim"]
    tier_3:
      name: "Lõi Kết Cấu Tối Ưu"
      effect: "Máu tàu +20%"
      cost: 1600 research
      requires: ["Vật Liệu Siêu Bền"]

  fleet_evasion:
    tier_1:
      name: "Động Cơ Hồi Đáp Nhanh"
      effect: "Né tránh +5%"
      cost: 200 research
    tier_2:
      name: "Ổn Định Phản Lực"
      effect: "Né tránh +10%"
      cost: 600 research
      requires: ["Động Cơ Hồi Đáp Nhanh"]

  shield_upgrade:
    tier_1:
      name: "Khiên Tầng Mỏng"
      effect: "Khiên +10%"
      cost: 200 research
    tier_2:
      name: "Tụ Năng Lượng Tối Ưu"
      effect: "Khiên +20%"
      cost: 700 research
      requires: ["Khiên Tầng Mỏng"]

=== STATION UPGRADE REQUIREMENTS ===

STATION_UPGRADE:
  level_1:
    name: "Outpost"
    requirement: "Không yêu cầu"
    cost:
      metal: 300
      gas: 100
  level_2:
    name: "Defense Station"
    requirement: "Công nghệ: Cơ Khí Cơ Bản"
    cost:
      metal: 600
      gas: 200
      crystal: 100
  level_3:
    name: "Star Fortress"
    requirement: "Công nghệ: AI Điều Hành Xây Dựng"
    cost:
      metal: 1500
      gas: 600
      crystal: 300
      exotic: 5
  level_4:
    name: "Citadel"
    requirement: "Công nghệ: Nano Lắp Ghép"
    cost:
      metal: 3000
      gas: 1200
      crystal: 500
      exotic: 15
      nanite: 20

=== STATION MODULES ===

STATION_MODULES:

  shipyard:
    name: "Xưởng Đóng Tàu"
    effect: "+1 hàng đóng tàu"
    cost: { metal: 300, gas: 80 }

  advanced_shipyard:
    name: "Xưởng Đóng Tàu Cao Cấp"
    effect: "+2 hàng đóng tàu, +15% tốc độ xây"
    requires: ["Nano Lắp Ghép"]
    cost: { metal: 700, gas: 150, crystal: 50 }

  radar:
    name: "Trạm Radar"
    effect: "+20% tầm nhìn, phát hiện sớm tàu địch"
    cost: { metal: 150, gas: 50 }

  sensor_array:
    name: "Mảng Cảm Biến"
    effect: "+40% phát hiện địch"
    requires: ["Máy Tính Lượng Tử"]
    cost: { metal: 300, gas: 100, crystal: 30 }

  power_core:
    name: "Lò Năng Lượng"
    effect: "Tăng +20 năng lượng duy trì"
    cost: { metal: 200, gas: 100 }

  repair_bay:
    name: "Trạm Sửa Chữa"
    effect: "Tốc độ sửa chữa +30%"
    cost: { metal: 350, gas: 120, nanite: 10 }

  warehouse:
    name: "Kho Trung Tâm"
    effect: "+200 tải tài nguyên"
    cost: { metal: 400 }

  research_lab:
    name: "Phòng Thí Nghiệm"
    effect: "+10% tốc độ nghiên cứu"
    cost: { metal: 300, gas: 80, crystal: 20 }
