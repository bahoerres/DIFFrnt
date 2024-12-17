---
created: 2024-12-08T11:55
updated: 2024-12-08T11:55
---
# Dictionaries in Python: Storing Data in Key-Value Pairs

Created: 2024-09-24 19:15:12 UTC
Updated: 2024-09-25 01:08:00 UTC
UUID: 4b8c54cd-a1a2-403a-a6f7-fc1018462b85
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-09-24 19:15:19 UTC

Dictionaries
Dictionaries in Python are used to store data values in `key` -> `value` pairs. Dictionaries are a great way to store groups of information.

```python
# use curly braces
# add key-value pairs
car = {
  "brand": "Tesla",
  "model": "3",
  "year": 2019
}

```

Here the `car` variable is assigned to a dictionary `{}` containing the keys `brand`, `model` and `year`. The keys' corresponding values are `Tesla`, `3` and `2019`.
Assignment
Complete the `get_character_record` function. It takes a character's `name`, `server`, `level`, and `rank` as individual inputs, and returns a dictionary with the following keys:
* `name`
* `server`
* `level`
* `rank`
* `id`
Create and return a dictionary with the input values assigned to the matching keys above. The `id` key maps to the `name` and the `server` inputs concatenated with a `#` in the middle for uniqueness. We can't have two `bloodwarrior123`'s on the same server!
For example, given:
* name = bloodwarrior123
* server = server1
Then the `id` field should be set to `bloodwarrior123#server1`. I recommend using an `f-string` to create the `id` field.


rom main import *
run_cases = [
    (
        "bloodwarrior123",
        "server1",
        5,
        1,
        {
            "name": "bloodwarrior123",
            "server": "server1",
            "level": 5,
            "rank": 1,
            "id": "bloodwarrior123#server1",
        },
    ),
    (
        "fronzenboi",
        "server2",
        2,
        1,
        {
            "name": "fronzenboi",
            "server": "server2",
            "level": 2,
            "rank": 1,
            "id": "fronzenboi#server2",
        },
    ),
]
submit_cases = run_cases + [
    (
        "slasher69",
        "server3",
        2,
        5,
        {
            "name": "slasher69",
            "server": "server3",
            "level": 2,
            "rank": 5,
            "id": "slasher69#server3",
        },
    ),
    (
        "icequeen",
        "server4",
        3,
        2,
        {
            "name": "icequeen",
            "server": "server4",
            "level": 3,
            "rank": 2,
            "id": "icequeen#server4",
        },
    ),
    (
        "shadowmaster",
        "server5",
        4,
        3,
        {
            "name": "shadowmaster",
            "server": "server5",
            "level": 4,
            "rank": 3,
            "id": "shadowmaster#server5",
        },
    ),
    (
        "silentslasher",
        "server6",
        5,
        4,
        {
            "name": "silentslasher",
            "server": "server6",
            "level": 5,
            "rank": 4,
            "id": "silentslasher#server6",
        },
    ),
    (
        "hypershadow",
        "server7",
        3,
        5,
        {
            "name": "hypershadow",
            "server": "server7",
            "level": 3,
            "rank": 5,
            "id": "hypershadow#server7",
        },
    ),
]
def test(name, server, level, rank, expected_output):
    try:
        result = get_character_record(name, server, level, rank)
        for key, value in expected_output.items():
            print(f"Expected: {key}: {value}")
            print(f"Actual:   {key}: {result[key]}\n")
            if result[key] != value:
                if type(result[key]) != type(value):
                    print(f"'{key}' values are different types!")
                    print(
                        f"Expected '{key}' to be of type {type(value).__name__}, but got {type(result[key]).__name__}"
                    )
                print("Fail")
                return False
        if result != expected_output:
            print("Result object is incorrect:")
            for key, value in result.items():
                print(f" * {key}: {value}")
            print("Fail")
            return False
        print("Pass")
        return True
    except Exception as e:
        print(f"Exception: {str(e)}")
        print("Fail")
        return False
def main():
    index = 0
    passed = 0
    failed = 0
    for test_case in test_cases:
        index += 1
        print("---------------------------------")
        print(f"Test Case #{index}\n")
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

**Assistant** - 2024-09-24 19:15:19 UTC

 Certainly! I'll provide the Python code for the `get_character_record` function based on the assignment requirements. Here's the implementation:

```python
def get_character_record(name, server, level, rank):
    return {
        "name": name,
        "server": server,
        "level": level,
        "rank": rank,
        "id": f"{name}#{server}"
    }
```

This function does the following:

1. It takes four parameters: `name`, `server`, `level`, and `rank`.
2. It creates and returns a dictionary with five key-value pairs:
   - The `name`, `server`, `level`, and `rank` keys are assigned their corresponding input values.
   - The `id` key is created using an f-string that concatenates the `name` and `server` inputs with a `#` in between.

This implementation meets all the requirements specified in the assignment:
- It creates a dictionary with the required keys.
- It assigns the input values to the matching keys.
- It creates an `id` field by concatenating the `name` and `server` with a `#` in between, using an f-string.

This code should pass all the test cases provided. It's simple and straightforward, making it suitable for an entry-level course while still demonstrating the use of dictionaries and f-strings in Python.

---

**Human** - 2024-09-25 01:06:23 UTC

seems like maybe a followup with that same code? 

Duplicate Keys
Because dictionaries rely on unique keys, you can't have two of the same key in the same dictionary. If you try to use the same key twice, the first value will simply be overwritten.
Assignment
Another developer on our team has introduced a bug by specifying duplicate keys in the dictionary! *Fix the bug.*
The `get_character_record` function takes a character's `name`, `server`, `level`, and `rank`. It should return a dictionary with the following fields:
* name
* server
* level
* rank
* id
Where the `id` is the `name` and the `server` concatenated together with a `#` in the middle for uniqueness. We can't have two `bloodwarrior123`'s on the same server!

---

**Assistant** - 2024-09-25 01:06:23 UTC

 I understand. It seems there's a bug in the existing code where duplicate keys have been introduced. Let's fix the `get_character_record` function to ensure there are no duplicate keys. Here's the corrected version:

```python
def get_character_record(name, server, level, rank):
    return {
        "name": name,
        "server": server,
        "level": level,
        "rank": rank,
        "id": f"{name}#{server}"
    }
```

This implementation:

1. Takes four parameters: `name`, `server`, `level`, and `rank`.
2. Creates and returns a dictionary with five unique key-value pairs:
   - `"name"`: assigned the `name` input
   - `"server"`: assigned the `server` input
   - `"level"`: assigned the `level` input
   - `"rank"`: assigned the `rank` input
   - `"id"`: created by concatenating `name` and `server` with a `#` in between using an f-string

This code ensures that:
- Each key in the dictionary is unique.
- The `id` field is correctly formed by combining the `name` and `server`.
- There are no duplicate keys that would cause values to be overwritten.

This implementation should resolve any issues with duplicate keys and meet all the requirements specified in the assignment. It maintains the simplicity needed for an entry-level course while demonstrating proper use of dictionaries in Python.

---

**Human** - 2024-09-25 01:08:00 UTC

well, to be safe, below is the provided code:

def get_character_record(name, server, level, rank):
    return {
        "name": name,
        "server": server,
        "level": level,
        "level": 1,
        "rank": rank,
        "rank": 2,
        "id": f"{name}#{server}",
    }

---

**Assistant** - 2024-09-25 01:08:00 UTC

 Ah, I see. Thank you for providing the actual code. Now I can clearly see the bug with the duplicate keys. Let's fix this:

```python
def get_character_record(name, server, level, rank):
    return {
        "name": name,
        "server": server,
        "level": level,
        "rank": rank,
        "id": f"{name}#{server}"
    }
```

Here's what I changed:

1. Removed the duplicate `"level"` key with the hardcoded value of 1.
2. Removed the duplicate `"rank"` key with the hardcoded value of 2.

The bug was that the original function had duplicate keys for `"level"` and `"rank"`. In Python dictionaries, when you have duplicate keys, the last one overwrites all previous ones. This was causing the function to always return a level of 1 and a rank of 2, regardless of the input values.

This corrected version:
- Uses all four input parameters (`name`, `server`, `level`, and `rank`).
- Creates a dictionary with five unique keys.
- Correctly assigns the input values to their respective keys.
- Creates the `id` field by concatenating `name` and `server` with a `#` in between.

This fix ensures that the function works as intended, using the actual input values for `level` and `rank` instead of overwriting them with hardcoded values.

---

