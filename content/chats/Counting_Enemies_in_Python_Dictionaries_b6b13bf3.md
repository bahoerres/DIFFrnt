---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Counting Enemies in Python Dictionaries

Created: 2024-09-25 01:20:55 UTC
Updated: 2024-09-25 05:02:01 UTC
UUID: b6b13bf3-7fe8-49a8-b5d2-439ccf08a195
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-09-25 01:21:02 UTC

Counting Practice
Checking for existence
If you're unsure whether or not a key exists in a dictionary, use the in keyword.
cars = {
    "ford": "f150",
    "tesla": "3"
}
print("ford" in cars)
# Prints: True
print("gmc" in cars)
# Prints: False
Assignment
We need to be able to report to our players how many enemies are in their immediate vicinity - but they want the count of each enemy by its kind. Fix the count_enemies function. If you run the code, it will result in a KeyError. It takes a list of enemy_names as input. It should return a dictionary where the keys are all the enemy names from the list, and the values are the counts of how many times each enemy appeared in the list.

this is the code to be modified/corrected: 

def count_enemies(enemy_names):
    enemies_dict = {}
    for enemy_name in enemy_names:
        enemies_dict[enemy_name] += 1
    return enemies_dict

---

**Assistant** - 2024-09-25 01:21:02 UTC

 I understand you'd like me to provide a corrected version of the `count_enemies` function for an entry-level Python course. The current implementation has an issue that causes a KeyError. Let's fix it:

<antThinking>This code snippet is relatively short and part of an educational explanation, so it doesn't need to be in an artifact. We'll keep it in the main conversation for better context and easier follow-up questions.</antThinking>

Here's the corrected version of the function:

```python
def count_enemies(enemy_names):
    enemies_dict = {}
    for enemy_name in enemy_names:
        if enemy_name in enemies_dict:
            enemies_dict[enemy_name] += 1
        else:
            enemies_dict[enemy_name] = 1
    return enemies_dict
```

This corrected version addresses the KeyError issue by checking if the enemy_name is already in the dictionary before trying to increment its count. Here's a breakdown of the changes:

1. We still initialize an empty dictionary `enemies_dict`.
2. We iterate through each `enemy_name` in the `enemy_names` list.
3. For each `enemy_name`, we check if it's already in the dictionary using `if enemy_name in enemies_dict:`.
4. If it is, we increment its count by 1.
5. If it's not, we add it to the dictionary with an initial count of 1.
6. Finally, we return the completed dictionary.

This solution ensures that each enemy name is properly counted without raising a KeyError when encountering a new enemy name.

Would you like me to explain any part of this solution in more detail?

---

**Assistant** - 2024-09-25 01:26:47 UTC

 Certainly! I'll provide the implementation for the `get_most_common_enemy` function based on the assignment requirements. Here's the code:

<antThinking>This function is relatively short and part of an educational exercise. It doesn't need to be in an artifact, as it's better to keep it in the main conversation for easier discussion and follow-up questions.</antThinking>

```python
def get_most_common_enemy(enemies_dict):
    if not enemies_dict:
        return None
    
    max_count = float("-inf")
    most_common_enemy = None
    
    for enemy, count in enemies_dict.items():
        if count > max_count:
            max_count = count
            most_common_enemy = enemy
    
    return most_common_enemy
```

Let's break down this implementation:

1. We first check if the `enemies_dict` is empty. If it is, we return `None` as specified in the assignment.

2. We initialize `max_count` with negative infinity (`float("-inf")`) as suggested in the tip. This ensures that any count in the dictionary will be greater than our initial value.

3. We also initialize `most_common_enemy` as `None`. This will store the name of the enemy with the highest count.

4. We then iterate over the `enemies_dict` using the `.items()` method, which gives us both the enemy name (key) and count (value) in each iteration.

5. For each enemy, we check if its count is greater than the current `max_count`. If it is, we update `max_count` and `most_common_enemy`.

6. After the loop, `most_common_enemy` will contain the name of the enemy with the highest count, which we return.

This implementation efficiently finds the most common enemy in a single pass through the dictionary, handling all the cases specified in the assignment, including empty dictionaries and ties (it will return the first enemy encountered with the highest count in case of a tie).

Would you like me to explain any part of this solution in more detail?

---

**Human** - 2024-09-25 01:26:47 UTC

Iterating over a dictionary in Python
We can iterate over a dictionary's keys using the same no-index syntax we used to iterate over the values in a list. With access to the dictionary's keys, we also have access to their corresponding values.

```python
fruit_sizes = {
    "apple": "small",
    "banana": "large",
    "grape": "tiny"
}

for name in fruit_sizes:
    size = fruit_sizes[name]
    print(f"name: {name}, size: {size}")

# name: apple, size: small
# name: banana, size: large
# name: grape, size: tiny

```

*Note: we could have just as easily set the *`name` variable to `key` or simply `k`.
Assignment
We need to display on our player's screens what the most common enemy in a given area of the game map is.
Complete the `get_most_common_enemy` function by iterating over all enemies in the dictionary and returning only the *name* of the enemy with the highest count. If there are no enemies, return `None`.
`enemies_dict` is a dictionary of `name` -> `count`.
Tip: Negative infinity
When you're trying to find a "max" value, it helps to keep track of the "max so far" in a variable and to start that variable at the lowest possible number, negative infinity.

```py
max_so_far = float("-inf")

```

You'll also want to keep track of the enemy name associated with the maximum count. I would set the default for that variable to `None`.


from main import *
run_cases = [
    ({"jackal": 4, "kobold": 3, "soldier": 10, "gremlin": 5}, "soldier"),
    ({"jackal": 1, "kobold": 3, "soldier": 2, "gremlin": 5}, "gremlin"),
]
submit_cases = run_cases + [
    ({"jackal": 2, "gremlin": 7}, "gremlin"),
    ({"jackal": 3}, "jackal"),
    ({}, None),
    ({"jackal": 5, "kobold": 3, "soldier": 10, "gremlin": 5, "dragon": 20}, "dragon"),
    ({"jackal": 5, "kobold": 3, "soldier": 2, "gremlin": 10, "dragon": 1}, "gremlin"),
]
def test(input1, expected_output):
    print("---------------------------------")
    print(f"Inputs: {input1}")
    print(f"Expecting: {expected_output}")
    result = get_most_common_enemy(input1)
    if result == "None":
        print('Actual: "None"')
    else:
        print(f"Actual: {result}")
    if result == expected_output:
        print("Pass")
        return True
    print("Fail")
    return False
def main():
    passed = 0
    failed = 0
    for test_case in test_cases:
        correct = test(*test_case)
        if correct:
            passed += 1
        else:
            failed += 1
    if failed == 0:
        print("============= PASS ==============")
    else:
        print("============= FAIL ==============")
    print(f"{passed} passed, {failed} failed")
test_cases = submit_cases
if "__RUN__" in globals():
    test_cases = run_cases
main()

---

**Human** - 2024-09-25 05:00:11 UTC

Quest status
Fantasy Quest needs a way to check the status of individual character's quest status. The game stores each character's progress in a nested data structure, and your job is to fetch the status of a particular quest.
Here's the structure of a `progress` dictionary:

```py
{
    "entity": {
        "character": {
            "name": "Kaladin",
            "quests": {
                "bridge_run": {
                    "status": "In Progress",
                },
                "talk_to_syl": {
                    "status": "Completed",
                },
            },
        }
    }
}

```

Assignment
Complete the `get_quest_status` function. It accepts a progress dictionary and returns the character's status in the `"Dragon_Slayer"` quest. Chain the keys to access the nested data.
Hint
If the value retrieved from a dictionary is itself a dictionary, how would you access its values?




            "entity": {
                "character": {
                    "name": "Archer Finn",
                    "quests": {
                        "Dragon_Slayer": {
                            "status": "Not Started",
                        },
                        "Goblin_Hunter": {
                            "status": "Completed",
                        },
                    },
                }
            }
        },
        "Not Started",
    ),
    (
        {
            "entity": {
                "character": {
                    "name": "Mage Elara",
                    "quests": {
                        "Dragon_Slayer": {
                            "status": "Failed",
                        },
                        "Goblin_Hunter": {
                            "status": "Completed",
                        },
                    },
                }
            }
        },
        "Failed",
    ),
    (
        {
            "entity": {
                "character": {
                    "name": "Rogue Talon",
                    "quests": {
                        "Dragon_Slayer": {
                            "status": "Completed",
                        },
                        "Goblin_Hunter": {
                            "status": "Not Started",
                        },
                    },
                }
            }
        },
        "Completed",
    ),
]
def test(input1, expected_output):
    print("---------------------------------")
    print(f"Inputs:")
    print(f" * Progress Dictionary: {input1}")
    print(f"Expecting: {expected_output}")
    result = get_quest_status(input1)
    print(f"Actual: {result}")
    if result == expected_output:
        print("Pass")
        return True
    print("Fail")
    return False
def main():
    passed = 0
    failed = 0
    for test_case in test_cases:
        correct = test(*test_case)
        if correct:
            passed += 1
        else:
            failed += 1
    if failed == 0:
        print("============= PASS ==============")
    else:
        print("============= FAIL ==============")
    print(f"{passed} passed, {failed} failed")
test_cases = submit_cases
if "__RUN__" in globals():
    test_cases = run_cases
main()

---

**Assistant** - 2024-09-25 05:00:11 UTC

 Based on the assignment requirements, I'll implement the `get_quest_status` function to retrieve the status of the "Dragon_Slayer" quest from the nested dictionary structure. Here's the code:

<antThinking>This function is relatively short and part of an educational exercise. It doesn't need to be in an artifact, as it's better to keep it in the main conversation for easier discussion and follow-up questions.</antThinking>

```python
def get_quest_status(progress):
    return progress["entity"]["character"]["quests"]["Dragon_Slayer"]["status"]
```

Let's break down this implementation:

1. We start with the `progress` dictionary.
2. We access the "entity" key, which gives us another dictionary.
3. From there, we access the "character" key, which gives us yet another dictionary.
4. We then access the "quests" key, giving us a dictionary of quests.
5. We specifically access the "Dragon_Slayer" quest.
6. Finally, we access the "status" of the Dragon_Slayer quest.

This chain of key accesses allows us to navigate through the nested structure and retrieve the specific status we're looking for.

It's worth noting that this implementation assumes the structure is always present and correct. In a more robust implementation, you might want to add error handling to deal with cases where a key might be missing. For example:

```python
def get_quest_status(progress):
    try:
        return progress["entity"]["character"]["quests"]["Dragon_Slayer"]["status"]
    except KeyError:
        return "Quest not found"
```

This version would return "Quest not found" if any part of the path is missing, rather than raising an error.

Would you like me to explain any part of this solution in more detail?

---

**Human** - 2024-09-25 05:02:01 UTC

This time we'll just roll with the assignment description: 

Total Score
The recently added Fantasy Quest battlegrounds are having issues with their in-game score due to how the data is being stored. The first-half score and second-half score are stored in separate dictionaries, making it difficult for them to parse the overall score. You've been asked to write a function that merges the two dictionaries and another function that calculates the total score.
Assignment
Complete the `merge` and `total_score` functions.
`merge`
This function accepts two score dictionaries as input and returns a single *merged* dictionary that contains all of the keys and values from the input dictionaries.
If a key exists in both dictionaries, the value from the second dictionary should overwrite the value from the first dictionary. For example:

```py
two_towers = {"Frodo": "One Ring", "Aragorn": "Narsil"}
rotk = {"Aragorn": "Andúril", "Gandalf": "Glamdring"}
merged_dict = merge(two_towers, rotk)
print(merged_dict)
# {'Frodo': 'One Ring', 'Aragorn': 'Andúril', 'Gandalf': 'Glamdring'}

```

`total_score`
This function should take a *single* score dictionary as input and return the total score calculated from the values of that dictionary.
If no points were scored, the function should return `0`.
*Don't forget: you can always add *`print()` statements to your code so that you can debug your code before submitting! Print out values of variables to see what's going on, and question your assumptions about what you think is happening.
Example of debugging with print statements

```python
def total_score(score_dict):
    print(f"score_dict: {score_dict}")
    for key in score_dict:
        print(f"key: {key}")

```

You would then run your code and manually inspect the output to see what's going on. You can always remove the print statements when you're done debugging if you want.

---

**Assistant** - 2024-09-25 05:02:01 UTC

 Certainly! I'll implement both the `merge` and `total_score` functions based on the assignment description. Here's the code for both functions:

<antThinking>These functions are relatively short and part of an educational exercise. They don't need to be in an artifact, as it's better to keep them in the main conversation for easier discussion and follow-up questions.</antThinking>

```python
def merge(dict1, dict2):
    merged = dict1.copy()
    merged.update(dict2)
    return merged

def total_score(score_dict):
    return sum(score_dict.values())
```

Let's break down each function:

1. `merge` function:
   - We start by creating a copy of `dict1` using the `copy()` method. This ensures we don't modify the original dictionary.
   - We then use the `update()` method to add all key-value pairs from `dict2` to our copy of `dict1`.
   - If there are any keys in `dict2` that also exist in `dict1`, their values will be overwritten by the values from `dict2`.
   - Finally, we return the merged dictionary.

2. `total_score` function:
   - We use the `sum()` function to add up all the values in the `score_dict`.
   - The `values()` method of the dictionary gives us all the values, which we then sum up.
   - If the dictionary is empty (no points scored), `sum()` will return 0, satisfying the requirement to return 0 if no points were scored.

These implementations should work for the given requirements. The `merge` function will combine two dictionaries, with the second dictionary's values taking precedence in case of key conflicts. The `total_score` function will sum up all the scores in a single dictionary.

Would you like me to explain any part of these solutions in more detail or add any debugging print statements?

---

