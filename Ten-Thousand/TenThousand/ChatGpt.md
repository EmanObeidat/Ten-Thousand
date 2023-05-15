# ChatGPT
## prompt1
Define a GameLogic class in ten_thousand/game_logic.py file.

Handle calculating score for dice roll

Add calculate_score static method to GameLogic class.

The input to calculate_score is a tuple of integers that represent a dice roll.

The output from calculate_score is an integer representing the roll’s score according to rules of game.
## The response:
**It gives 5 failed and 16 passed**
```
class GameLogic:
    @staticmethod
    def calculate_score(roll):
        score = 0
        dice_counts = [0] * 7  # Initialize counts for each dice face (1 to 6)

        for die in roll:
            dice_counts[die] += 1

        # Calculate score based on the counts of each dice face
        for face, count in enumerate(dice_counts):
            if count >= 3:
                if face == 1:
                    score += 1000
                else:
                    score += face * 100

                count -= 3  # Reduce the count of the scored dice

            if face == 1:
                score += count * 100
            elif face == 5:
                score += count * 50

        return score
```


# prompt 2
Add roll_dice static method to GameLogic class.

The input to roll_dice is an integer between 1 and 6.

The output of roll_dice is a tuple with random values between 1 and 6.
The length of tuple must match the argument given to roll_dice method.

**The  Response:**
```
@staticmethod
    def roll_dice(num_dice):
        if num_dice < 1 or num_dice > 6:
            raise ValueError("Number of dice must be between 1 and 6.")

        dice = tuple(random.randint(1, 6) for _ in range(num_dice))
        return dice
```
## The failed message of all previuos codes:
```
FAILED tests/version1/test_calculate_score.py::test_straight - assert 150 == 1500
FAILED tests/version1/test_calculate_score.py::test_four_of_a_kind - assert 200 == 400
FAILED tests/version1/test_calculate_score.py::test_five_of_a_kind - assert 200 == 600
FAILED tests/version1/test_calculate_score.py::test_six_of_a_kind - assert 200 == 800
FAILED tests/version1/test_calculate_score.py::test_six_ones - assert 1300 == 4000
```