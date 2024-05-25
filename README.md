# Hangman-Game
# Author - Anik Chand

import random as r
import os

print('''
****************************************************
************* WELCOME TO HANGMAN GAME **************
****************************************************
''')
print('''

██╗░░██╗░█████╗░███╗░░██╗░██████╗░███╗░░░███╗░█████╗░███╗░░██╗
██║░░██║██╔══██╗████╗░██║██╔════╝░████╗░████║██╔══██╗████╗░██║
███████║███████║██╔██╗██║██║░░██╗░██╔████╔██║███████║██╔██╗██║
██╔══██║██╔══██║██║╚████║██║░░╚██╗██║╚██╔╝██║██╔══██║██║╚████║
██║░░██║██║░░██║██║░╚███║╚██████╔╝██║░╚═╝░██║██║░░██║██║░╚███║
╚═╝░░╚═╝╚═╝░░╚═╝╚═╝░░╚══╝░╚═════╝░╚═╝░░░░░╚═╝╚═╝░░╚═╝╚═╝░░╚══╝

''')
sports_words = [
    "football", "soccer", "basketball", "baseball", "tennis", "golf", "cricket",
    "rugby", "hockey", "volleyball", "badminton", "boxing", "swimming", "running",
    "cycling", "surfing", "skiing", "snowboarding", "wrestling", "karate", "judo",
    "fencing", "gymnastics", "archery", "weightlifting", "rowing", "sailing",
    "climbing", "skydiving", "paragliding"
]
food_words = [
    "apple", "banana", "orange", "grape", "strawberry", "blueberry", "watermelon",
    "melon", "pineapple", "peach", "pear", "kiwi", "plum", "cherry", "mango",
    "lemon", "lime", "coconut", "avocado", "tomato", "potato", "carrot", "onion",
    "garlic", "ginger", "lettuce", "cucumber", "spinach", "broccoli", "cauliflower",
    "cabbage", "pepper", "eggplant", "zucchini", "pumpkin", "sweetpotato", "corn",
    "bean", "pea", "rice", "pasta", "bread", "cake", "cookie", "chocolate", "icecream",
    "cheese", "milk", "butter", "yogurt", "cream", "jam", "honey", "sugar", "salt",
    "pepper", "oil", "vinegar", "sauce", "mustard", "ketchup", "mayonnaise", "spice"
]
animal_words = [
    "dog", "cat", "horse", "elephant", "lion", "tiger", "bear", "zebra", "giraffe",
    "monkey", "gorilla", "chimpanzee", "kangaroo", "koala", "panda", "wolf",
    "fox", "deer", "rabbit", "squirrel", "mouse", "rat", "hamster", "guinea pig",
    "parrot", "penguin", "eagle", "hawk", "owl", "seagull", "duck", "swan",
    "goose", "chicken", "rooster", "turkey", "cow", "bull", "buffalo", "ox",
    "sheep", "goat", "pig", "horse", "donkey", "mule", "camel", "llama",
    "alpaca", "elephant", "rhinoceros", "hippopotamus", "giraffe", "zebra",
    "kangaroo", "koala", "panda", "sloth", "armadillo", "anteater", "toucan",
    "gorilla", "orangutan", "lemur", "baboon", "hyena", "cheetah", "leopard",
    "jaguar", "panther", "cougar", "lynx", "bobcat", "wolverine", "badger",
    "weasel", "otter", "ferret", "mongoose", "raccoon", "skunk", "possum",
    "chipmunk", "beaver", "porcupine", "hedgehog", "mole", "shrew", "bat"
]
place_names= [
    'newyork', 'london', 'paris', 'tokyo', 'berlin', 'sydney', 'rome',
    'madrid', 'moscow', 'toronto', 'chicago', 'riodejaneiro', 'hongkong',
    'dubai', 'singapore', 'amsterdam', 'seoul', 'bangkok', 'mumbai', 'beijing',
    'shanghai', 'istanbul', 'cairo', 'mexicocity', 'barcelona', 'vienna',
    'budapest', 'prague', 'athens', 'stockholm', 'copenhagen', 'oslo',
    'helsinki', 'warsaw', 'dublin', 'brussels', 'lisbon', 'geneva', 'zurich',
    'venice', 'florence', 'milan', 'naples', 'dubrovnik', 'buenosaires', 'saopaulo',
    'lima', 'bogota', 'santiago', 'capetown', 'johannesburg', 'auckland', 'wellington',
    'christchurch', 'perth', 'adelaide', 'brisbane', 'melbourne', 'vancouver', 'montreal',
    'quebeccity', 'calgary', 'edmonton', 'ottawa', 'halifax', 'sydney', 'melbourne',
    'brisbane', 'adelaide', 'perth', 'goldcoast', 'canberra', 'hobart', 'darwin',
     'auckland', 'wellington', 'christchurch'
]

profession_words = [
    "doctor", "nurse", "teacher", "engineer", "scientist", "lawyer", "programmer",
    "artist", "musician", "actor", "chef", "architect", "writer", "journalist",
    "designer", "pilot", "firefighter", "police officer", "soldier", "veterinarian",
    "dentist", "pharmacist", "psychologist", "accountant", "electrician", "plumber",
    "mechanic", "carpenter", "welder", "construction worker", "chef", "barista",
    "waiter", "bartender", "tailor", "hairdresser", "makeup artist", "photographer",
    "filmmaker", "athlete", "coach", "trainer", "nutritionist", "physiotherapist",
    "surgeon", "anesthesiologist", "gynecologist", "pediatrician", "dermatologist",
    "ophthalmologist", "psychiatrist", "radiologist", "phlebotomist", "paramedic",
    "ambulance driver", "nanny", "babysitter", "caretaker", "housekeeper",
    "cleaner", "gardener", "farmer",
    "zookeeper",
    "courier"
]
subject_words= [
    'mathematics', 'physics', 'chemistry', 'biology', 'geology', 'astronomy',
    'computer science', 'engineering', 'medicine', 'psychology', 'sociology',
    'anthropology', 'linguistics', 'literature', 'history', 'art', 'music',
    'philosophy', 'economics', 'politicalscience', 'environmental science',
    'geography', 'law', 'business', 'management', 'marketing', 'finance',
    'accounting', 'education', 'communication', 'journalism', 'architecture',
    'nutrition', 'publichealth', 'nursing',
    'physiotherapy', 'pharmacy', 'dentistry',
    'agriculture', 'horticulture', 'forestry', 'aquaculture', 'marinebiology', 'zoology',
    'botany', 'microbiology', 'biotechnology', 'biochemistry', 'genetics', 'cellbiology',
    'ecology', 'psychiatry', 'neuroscience',
    'artificialintelligence', 'machinelearning', 'robotics', 'data science', 'statistics',
    'econometrics', 'gametheory', 'ethics', 'theology', 'religiousstudies', 'mythology',
    'folklore', 'literarytheory', 'filmstudies', 'performingarts', 'dance', 'drama',
    'theater', 'film', 'cinema', 'fashiondesign', 'graphicdesign', 'industrialdesign',
    'interiordesign', 'productdesign', 'visualarts', 'finearts', 'sculpture', 'painting'
]

transport_words = [
    "car", "truck", "bus", "bike", "motorcycle", "scooter", "van", "minivan",
    "taxi", "limousine", "train", "subway", "tram", "metro", "lightrail",
    "monorail", "trolleybus", "ferry", "boat", "ship",
    "sailboat", "yacht", "canoe", "kayak", "raft", "jetski", "hovercraft",
    "airplane", "helicopter", "glider", "paraglider",
    "hotairballoon", "blimp", "zeppelin", "bicycle", "skateboard",
    "rollerblades", "scooter", "wheelchair", "stroller",
    "segway", "electric car",
    "backhoe", "excavator", "crane", "forklift", "tractor",
    "combineharvester", "mower", "tugboat"
]
tech_science_words = [
    "computer", "software", "hardware", "internet", "website", "database", "server",
    "network", "programming", "coding", "algorithm", "data",
    "robotics", "automation", "augmented reality",
    "smartphone", "tablet", "laptop", "desktop", "monitor",
    "keyboard", "mouse", "printer", "scanner", "router", "modem", "firewall",
    "encryption", "cybersecurity", "biotechnology", "genetic engineering", "DNA",
    "RNA", "genome", "gene", "protein", "cell", "microorganism", "virus", "bacteria",
    "fungus", "microbiology", "biochemistry", "chemistry", "physics", "biology",
    "astronomy", "astrophysics", "cosmology", "geology", "meteorology", "oceanography",
    "paleontology", "ecology", "geography",
    "optics", "thermodynamics", "telecommunications"
]
medical_science_words = [
    "dna","rna","hiv","aid","tb","bmi","ct","mri",
    "anatomy", "physiology", "pathology", "pharmacology", "microbiology", "immunology",
    "genetics", "biochemistry", "histology", "embryology", "neuroscience", "endocrinology",
    "cardiology", "pulmonology", "gastroenterology", "hepatology", "nephrology",
    "urology", "hematology", "oncology", "radiology", "neuroradiology",
    "dermatology", "ophthalmology", "otolaryngology", "audiology",
    "dentistry", "orthodontics", "periodontics", "prosthodontics",
    "orthopedics", "rheumatology",
    "pediatrics", "neonatology", "geriatrics", "obstetrics", "gynecology", "midwifery",
    "perinatology", "psychiatry", "psychology", "psychotherapy", "counseling",
    "neurology", "neurosurgery", "anesthesiology"
]
entertainment_hobbies_words =[
    "music", "movie", "film", "cinema", "television", "series", "episode",
    "documentary", "animation", "cartoon", "anime", "comic",
    "chess", "checkers", "dominoes", "mahjong",
    "podcast", "audiobook", "radio", "theater", "play", "musical", "opera",
    "concert", "festival", "improv",
    "magic", "circus", "dance", "ballet",
    "hiking", "camping", "backpacking", "biking", "cycling", "running",
    "jogging", "walking", "swimming", "surfing", "skateboarding", "rollerblading",
    "skating", "skiing", "snowboarding", "snowshoeing",
    "bouldering", "mountaineering", "fishing",
    "gardening", "landscaping", "flower arranging", "cooking", "baking", "grilling",
    "mixology", "painting", "drawing", "sketching", "sculpting", "pottery", "ceramics",
    "jewelry making", "knitting", "crocheting", "sewing", "quilting", "embroidery",
    "weaving", "macramé", "woodworking", "carpentry", "metalworking", "blacksmithing",
    "photography", "videography", "filmmaking", "editing",
    "writing", "reading", "novel", "fiction",
    "essay", "journalism", "blogging", "vlogging", "travel", "exploration",
    "adventure", "sightseeing", "tourism", "cruising", "backpacking"
]
sci_fi_fantasy_words = [
    "fantasy", "space", "spaceship", "alien", "extraterrestrial",
    "planet", "galaxy", "universe", "wormhole",
    "teleportation", "hyperspace", "cyberspace", "reality",
    "intelligence", "robot", "android", "cyborg", "clone", "nanotechnology",
    "engineering", "bioengineering", "mutant", "superhuman", "superpower",
    "magic", "wizard", "sorcerer", "witch", "mage", "warlock", "dragon", "elf", "dwarf",
    "orc", "goblin", "troll", "fairy", "sprite", "mermaid", "unicorn", "centaur", "vampire",
    "werewolf", "zombie", "ghost", "demon", "angel", "giant", "monster", "creature",
    "invasion", "apocalypse", "dystopia", "utopia", "cyberpunk",
    "steampunk", "machine", "technology", "empire",
    "alliance", "starship", "starfighter", "lightsaber", "force", "telekinesis",
    "control", "psychic", "paranormal", "supernatural", "mystical", "enchanted",
    "portal", "wand", "spell", "incantation", "ritual", "summoning", "alchemy",
    "sorcery", "necromancy", "conjure", "enchantment", "hex", "curse", "prophecy",
    "quest", "adventure", "hero", "heroine", "villain", "antihero", "quest",
    "journey", "chosen", "destiny", "fate", "savior", "chosen", "resistance",
    "revolution", "rebellion", "movement", "federation", "alliance",
    "confederation", "empire", "kingdom", "realm", "dominion", "domain", "worldbuilding"
]
nature_environment_words = [
    "nature", "environment", "ecosystem", "habitat", "biome", "forest", "jungle",
    "rainforest", "woodland", "savanna", "grassland", "prairie", "desert",
    "tundra", "arctic", "antarctic", "ocean", "sea", "river", "lake", "pond",
    "stream", "creek", "waterfall", "glacier", "mountain", "hill", "valley",
    "plateau", "canyon", "volcano", "island", "peninsula", "coast", "beach",
    "shore", "coral reef", "wetland", "marsh", "swamp", "bog", "fen", "estuary",
    "delta", "mangrove", "cave", "cavern", "grotto", "geyser", "spring"
]
history_culture_words = [
    "history", "culture", "civilization", "ancient", "medieval", "renaissance",
    "modern", "contemporary", "archaeology", "anthropology", "sociology",
    "historiography", "artifact", "ruins", "monument", "landmark", "heritage",
    "tradition", "custom", "ritual", "ceremony", "celebration", "festivity",
    "holiday", "folklore", "mythology", "legend", "tale", "tradition",
    "exchange", "assimilation", "identity", "diversity", "heritage",
    "preservation", "appropriation", "diffusion", "imperialism", "revolution"
]
emotions_words = [
    "happy", "sad", "angry", "excited", "nervous", "surprised",
    "confused", "relaxed", "anxious", "joyful", "sorrowful",
    "frustrated", "energetic", "calm", "peaceful", "hopeful", "proud",
    "embarrassed", "grateful", "sympathetic", "empathetic", "disappointed",
    "satisfied", "lonely", "loved", "hated", "bored", "enthusiastic",
    "ecstatic", "depressed", "melancholy", "gloomy", "optimistic", "pessimistic",
    "overwhelmed", "envious", "jealous", "resentful", "ashamed", "guilty",
    "regretful", "remorseful", "serene", "blissful", "contented", "miserable",
    "desperate", "elated", "euphoric", "apathetic", "indifferent", "thankful",
    "graceful", "cheerful", "merry", "jovial", "gleeful", "zestful", "lively",
    "vibrant", "playful", "carefree", "mirthful", "humble", "pensive", "reflective",
    "introspective", "melancholic", "sentimental", "nostalgic", "compassionate",
    "affectionate", "tender"
]

hangman = [
    r"""
      +---+
          |  
          |
          |
          |
          |
    """,
    r"""
      +---+
      |   |  
      O   |
          |
          |
          |
    """,
    r"""
      +---+
      |   |  
      O   |
      |   |
          |
          | 
    """,
    r"""
      +---+
      |   |  
      O   | 
     /|   | 
          | 
          |
    """,
    r"""
      +---+
      |   |  
      O   | 
     /|\  | 
          |
          |
    """,
    r"""
      +---+
      |   |  
      O   | 
     /|\  | 
     /    | 
          |
    """,
    r"""
      +---+
      |   |  
      O   | 
     /|\  | 
     / \  | 
          | ☠️
    """
]

print('''
PLEASE READ THE FOLLOWING INSTRUCTIONS CAREFULLY BEFORE PLAYING THE GAME:

* It is a word guessing game.
* You will be provided with a domain of the word you have to guess.
* Each turn, you must input a single letter to attempt to complete the word.
* You will start with 6 lives. If your chosen letter is in the word, your lives will 
  remain the same, and the letter will automatically be placed in its correct position. 
  However, for each incorrect guess, you will lose 1 life.
* You must guess the word before your remaining lives reach 0, or you will lose the game.
* At the conclusion of the game, the actual word will be revealed to you.
* Additionally, you will receive a summary of your game performance.

Please proceed and enjoy the game!
''')
while True:
    name = input('enter player name(Only 1st name w/o space): ').title()
    if name.isalpha():
        break
    else:
        print('enter valid name')
print(f"{name}, let's start.")

def hangman_main_fn():
    print('''
    DIFFICULTY LEVELS:
    easy(2-4 letters)
    moderate(5-7 letters)
    hard(more than 7 letters)
    ''')

    while True:
        difficulty_level = input('Choose difficulty level- easy/moderate/hard : ').lower()
        if difficulty_level.isalpha():
            break
        if difficulty_level == 'easy' or difficulty_level == 'moderate' or difficulty_level == 'hard':
            break
        else:
            print('enter valid input')

    print('GREAT CHOICE')


    def generate_topic():
        category = {
            tuple(profession_words): 'Professions',
            tuple(place_names): 'Places',
            tuple(animal_words): 'Animals',
            tuple(food_words): 'Foods',
            tuple(sports_words): 'Sports',
            tuple(subject_words): 'Subjects',
            tuple(tech_science_words): 'Technology and Science',
            tuple(medical_science_words): 'Medical Science',
            tuple(entertainment_hobbies_words): 'Entertainment & Hobbies',
            tuple(sci_fi_fantasy_words): 'Science Fiction & Fantasy',
            tuple(nature_environment_words): 'Nature & Environment',
            tuple(history_culture_words): 'History & Culture',
            tuple(emotions_words): 'Emotions'
        }

        category_choice = r.choice(list(category.keys()))

        return category[category_choice], category_choice


    t, key = generate_topic()
    print(f'Domain of your word is: {t}')


    def select_word1(key):
        filtered_words = []
        for i in key:
            if len(i) < 5:
                filtered_words.append(i)
        return r.choice(filtered_words)


    def select_word2(key):
        filtered_words = []
        for i in key:
            if len(i) >= 5 and len(i) < 8:
                filtered_words.append(i)
        return r.choice(filtered_words)


    def select_word3(key):
        filtered_words = []
        for i in key:
            if len(i) >= 8:
                filtered_words.append(i)
        return r.choice(filtered_words)


    if difficulty_level == 'easy':
        select_word = select_word1(key)
    elif difficulty_level == 'moderate':
        select_word = select_word2(key)
    elif difficulty_level == 'hard':
        select_word = select_word3(key)
    else:
        print('please enter valid input')

    letter_numbers = len(select_word)
    print(f'you have to guess a {letter_numbers} letter word...')
    list_word = []

    for i in range(letter_numbers):
        list_word.append('_')

    print(''.join(list_word))

    life = 6
    print(f'life: {life}')

    correct_attampts = 0
    wrong_attampts = 0
    while '_' in list_word and life > 0:
        if life == 6:
            print(hangman[0])
        elif life == 5:
            print(hangman[1])
        elif life == 4:
            print(hangman[2])
        elif life == 3:
            print(hangman[3])
        elif life == 2:
            print(hangman[4])
        else:
            print(hangman[5])

        while True:
            g = input('guess a letter: ').lower()
            if len(g) == 1 and g.isalpha():
                break
            else:
                print('enter valid input')

        if g in select_word:
            for i in range(letter_numbers):
                if g == select_word[i]:
                    list_word[i] = g
            correct_attampts += 1
        else:
            life -= 1
            wrong_attampts += 1

        print(''.join(list_word))
        print(f'life: {life}')

    if life == 0:
        print(hangman[6])
        print(f"game over . The word is: {''.join(select_word)}")
        print('''
    ⠀⠀⠀⠀⠀⠀⢀⣤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⢤⣤⣀⣀⡀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⢀⡼⠋⠀⣀⠄⡂⠍⣀⣒⣒⠂⠀⠬⠤⠤⠬⠍⠉⠝⠲⣄⡀⠀⠀
    ⠀⠀⠀⢀⡾⠁⠀⠊⢔⠕⠈⣀⣀⡀⠈⠆⠀⠀⠀⡍⠁⠀⠁⢂⠀⠈⣷⠀⠀
    ⠀⠀⣠⣾⠥⠀⠀⣠⢠⣞⣿⣿⣿⣉⠳⣄⠀⠀⣀⣤⣶⣶⣶⡄⠀⠀⣘⢦⡀
    ⢀⡞⡍⣠⠞⢋⡛⠶⠤⣤⠴⠚⠀⠈⠙⠁⠀⠀⢹⡏⠁⠀⣀⣠⠤⢤⡕⠱⣷
    ⠘⡇⠇⣯⠤⢾⡙⠲⢤⣀⡀⠤⠀⢲⡖⣂⣀⠀⠀⢙⣶⣄⠈⠉⣸⡄⠠⣠⡿
    ⠀⠹⣜⡪⠀⠈⢷⣦⣬⣏⠉⠛⠲⣮⣧⣁⣀⣀⠶⠞⢁⣀⣨⢶⢿⣧⠉⡼⠁
    ⠀⠀⠈⢷⡀⠀⠀⠳⣌⡟⠻⠷⣶⣧⣀⣀⣹⣉⣉⣿⣉⣉⣇⣼⣾⣿⠀⡇⠀
    ⠀⠀⠀⠈⢳⡄⠀⠀⠘⠳⣄⡀⡼⠈⠉⠛⡿⠿⠿⡿⠿⣿⢿⣿⣿⡇⠀⡇⠀
    ⠀⠀⠀⠀⠀⠙⢦⣕⠠⣒⠌⡙⠓⠶⠤⣤⣧⣀⣸⣇⣴⣧⠾⠾⠋⠀⠀⡇⠀
    ⠀⠀⠀⠀⠀⠀⠀⠈⠙⠶⣭⣒⠩⠖⢠⣤⠄⠀⠀⠀⠀⠀⠠⠔⠁⡰⠀⣧⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠛⠲⢤⣀⣀⠉⠉⠀⠀⠀⠀⠀⠁⠀⣠⠏⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠉⠉⠛⠒⠲⠶⠤⠴⠒⠚⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
        ''')
    else:
        print('You won the game 😃!!')
        print('''
       ⢀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⠀⠀⠀⠀
    ⢠⣤⣤⣤⣼⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⣄⣤⣤⣠
    ⢸⠀⡶⠶⠾⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡷⠶⠶⡆⡼
    ⠈⡇⢷⠀⠀⣇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢰⠇⠀⢸⢁⡗
    ⠀⢹⡘⡆⠀⢹⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡸⠀⢀⡏⡼⠀
    ⠀⠀⢳⡙⣆⠈⣇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⠇⢀⠞⡼⠁⠀
    ⠀⠀⠀⠙⣌⠳⣼⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣞⡴⣫⠞⠀⠀⠀
    ⠀⠀⠀⠀⠈⠓⢮⣻⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⡼⣩⠞⠉⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠉⠛⣆⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⠞⠋⠁⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠳⢤⣀⠀⠀⠀⠀⢀⣠⠖⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠉⡇⢸⡏⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⢸⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⠖⠒⠓⠚⠓⠒⣦⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⣀⣠⣞⣉⣉⣉⣉⣉⣉⣉⣉⣉⣉⣙⣆⣀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  ⡇⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  ⠀⠀⡇⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠓⠲⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠖⠃⠀⠀⠀⠀⠀⠀
        ''')

    print(f'''
    GAME SUMMARY--
    Player name : {name}
    Difficulty level : {difficulty_level}
    lives used : {6 - life}
    Total attampts : {correct_attampts + wrong_attampts}
    Correct attampts : {correct_attampts}
    Wrong attampts : {wrong_attampts}
    ''')
    ask=input('Do you want to play the game again?- y/n: ')
    if ask=='y':
        os.system('cls')
        hangman_main_fn()

hangman_main_fn()
print('''
Thank you for playing the game.
Good Bye... 
''')

