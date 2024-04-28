# Guess Who? Best Questions

This repository came as a need after playing several games with my young sons. I decided to develop a model to find the best strategy for winning the game and hand over to them in order for my sons to become better players.

## Guess Who? Rules
For anyone that does not know how Guess Who? is played read the following (it is a really simple but interesting game):

According to [Hasbro's Official Instructions](https://instructions.hasbro.com/en-nz/instruction/Guess-Who--Classic-Game), each player chooses a mystery character and then using yes or no questions, they try to figure out the other player's mystery character. When they think they know who their opponent's mystery character is, players make a guess. If the guess is wrong, that player loses the game! Players can also challenge opponents to a series of games in the Championship Series, where the first player to win 5 games is the Guess Who? champion.

## Data
The data that this ML model was trained on originate from the &copy; 2018 Hasbro characters of the game, as shown in the figure taken from [Geeky Hobbies History of Guess Who? webpage](https://www.geekyhobbies.com/history-of-guess-who/).

![image](https://github.com/Lefteris-Souflas/Guess-Who-Best-Questions/assets/143879796/be7eedad-e712-4c29-a516-905935a8e9e4)

I created a [dataset](Guess-Who-Characters-Questions.csv) with all 24 characters in its rows with their English and Greek names (as the game was played in the Greek version of it by my kids) in the first 2 columns. The next 18 columns include a question per column with a Yes (1) or No (0) answer per character (row). A **summary** of all characteristics are presented in the figure below.

![Guess-Who-Characters-Summary](https://github.com/Lefteris-Souflas/Guess-Who-Best-Questions/assets/143879796/60a710dc-1e58-46d1-9ac5-aff3df44bd78)

Then, I inserted the dataset into an **Oracle Database**, as shown in the figure below. 

![Screenshot 2024-04-28 220634](https://github.com/Lefteris-Souflas/Guess-Who-Best-Questions/assets/143879796/3afc6074-92fe-4ea6-ac54-9a43cd94b6b7)

