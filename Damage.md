=== WEAPON TYPES (BASE STATS) ===
CANNON:
 - Damage: 120
 - Fire rate: 0.8
 - Accuracy: 0.75
 - Crit chance: 0.10
 - Hit bonus vs: Small -20%, Medium +0%, Heavy +20%, Capital +30%

LASER:
 - Damage: 90
 - Fire rate: 1.4
 - Accuracy: 0.90
 - Crit chance: 0.05
 - Hit bonus vs: Shield +40%, Armor -10%, Hull +10%

MISSILE:
 - Damage: 180
 - Fire rate: 0.5
 - Accuracy: 0.65
 - Crit chance: 0.15
 - Hit bonus vs: Large targets +35%, Small -30%
 - Ignores 20% armor

DRONE:
 - Damage: 40 (per drone)
 - Fire rate: 3.0
 - Accuracy: 0.85
 - Crit chance: 0.08
 - Hit bonus vs: Evasion -20%, Small +20%, Large -15%


=== DEFENSE STATS ===
ARMOR (Giáp):
 - Reduces incoming damage by: Armor / 4
 - Minimum reduction: 5%
 - Max reduction: 60%

SHIELD (Khiên):
 - Absorbs damage first
 - Takes full damage
 - Regenerates 3% per second out of combat

HULL (Máu):
 - Receives full damage after shield = 0
 - No regeneration

EVASION (Né tránh):
 - Chance to avoid hit entirely
 - Formula: HitChance = WeaponAccuracy * (1 - TargetEvasion)
 - Minimum hit chance: 20%

=== SHIP CLASS STATS ===
SMALL SHIP:
 - Armor: 20
 - Shield: 60
 - Hull: 80
 - Evasion: 0.25

LIGHT SHIP:
 - Armor: 40
 - Shield: 120
 - Hull: 150
 - Evasion: 0.18

MEDIUM SHIP:
 - Armor: 80
 - Shield: 300
 - Hull: 350
 - Evasion: 0.10

BATTLESHIP:
 - Armor: 140
 - Shield: 600
 - Hull: 800
 - Evasion: 0.04

DREADNOUGHT:
 - Armor: 240
 - Shield: 1000
 - Hull: 1600
 - Evasion: 0.02

SUPERNOVA SHIP:
 - Armor: 400
 - Shield: 2000
 - Hull: 4000
 - Evasion: 0.01


=== DAMAGE CALCULATION ===

1) HIT CHANCE:
 HitChance = Accuracy * (1 - TargetEvasion)
 If HitChance < 0.20 → HitChance = 0.20

2) DAMAGE REDUCTION FROM ARMOR:
 DamageAfterArmor = RawDamage * (1 - (Armor / 400))
 Clamp reduction between 5% → 60%

3) SHIELD INTERACTION:
 If Shield > 0 → Damage applies to Shield first
 If Damage > Shield → Remaining goes to Hull

4) CRITICAL HIT:
 CritDamage = BaseDamage * 1.5  
 FinalDamage = BaseDamage OR CritDamage  

5) CLASS MULTIPLIER:
 FinalDamage = FinalDamage * ShipTypeMultiplier

6) MISSILE ARMOR PEN:
 EffectiveArmor = Armor * 0.8

7) DRONE MULTI HITS:
 TotalDroneDamage = DamagePerDrone * NumberOfHits


=== SHIP TYPE MULTIPLIER TABLE ===
CANNON:
 - Small: 0.8
 - Light: 1.0
 - Medium: 1.0
 - Battleship: 1.2
 - Dreadnought: 1.3
 - Supernova: 1.4

LASER:
 - Small: 1.0
 - Light: 1.0
 - Medium: 1.1
 - Battleship: 1.1
 - Dreadnought: 1.15
 - Supernova: 1.2

MISSILE:
 - Small: 0.7
 - Light: 1.0
 - Medium: 1.2
 - Battleship: 1.35
 - Dreadnought: 1.4
 - Supernova: 1.5

DRONE:
 - Small: 1.2
 - Light: 1.1
 - Medium: 1.0
 - Battleship: 0.85
 - Dreadnought: 0.8
 - Supernova: 0.7
