import math

# נתוני השחקן שלי (מיקום על המסך)
my_x = 50
my_y = 50

# רשימת אויבים שהבוט "זיהה" על המסך (מיקומי X ו-Y)
enemies = [
    {"name": "Colt", "x": 80, "y": 20},
    {"name": "Shelly", "x": 10, "y": 90},
    {"name": "El Primo", "x": 55, "y": 55}
]

def find_closest_enemy(me_x, me_y, enemy_list):
    closest_dist = 9999
    target = None
    
    for enemy in enemy_list:
        # חישוב מרחק אווירי (משפט פיתגורס)
        distance = math.sqrt((enemy['x'] - me_x)**2 + (enemy['y'] - me_y)**2)
        
        if distance < closest_dist:
            closest_dist = distance
            target = enemy
            
    return target, closest_dist

# הפעלת הבוט
target, dist = find_closest_enemy(my_x, my_y, enemies)

if target:
    print(f"המטרה הכי קרובה היא: {target['name']}")
    print(f"מרחק מהמטרה: {dist:.2f}")
    print(f"פקודה לסקריפט: כוון לזווית של {target['name']} ותירה!")
