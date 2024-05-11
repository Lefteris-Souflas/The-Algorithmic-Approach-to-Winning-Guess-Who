# The Algorithmic Approach to Winning the "Guess Who?" Game

This repository emerges from the necessity observed during numerous sessions of playing the "Guess Who?" game with my children. Recognizing an opportunity to enhance their gameplay, I embarked on developing a model aimed at determining the optimal strategy for winning the game.

## Understanding the "Guess Who?" Game

For those unfamiliar with the mechanics of the "Guess Who?" game, it involves players selecting a mystery character each. Through a series of yes or no questions, players attempt to deduce the identity of their opponent's mystery character. A successful guess leads to victory, while an incorrect guess results in defeat. Furthermore, players can engage in a Championship Series, where the first to win 5 games claims the title of "Guess Who?" champion.

For detailed instructions, refer to [Hasbro's Official Instructions](https://instructions.hasbro.com/en-nz/instruction/Guess-Who--Classic-Game).

## Dataset Overview

Utilizing characters from the &copy; 2018 Hasbro collection, this machine learning (ML) model is trained on data extracted from the game, as shown in the figure taken from [Geeky Hobbies History of Guess Who? webpage](https://www.geekyhobbies.com/history-of-guess-who/).

![image](https://github.com/Lefteris-Souflas/Guess-Who-Best-Questions/assets/143879796/be7eedad-e712-4c29-a516-905935a8e9e4)

The [dataset](guess_who_dataset.csv), comprising 24 characters, includes their English and Greek names (pertaining to the Greek version of the game). Each character is described by a set of attributes, with a binary (Yes/No) value indicating their possession of each trait. A comprehensive **summary** of these attributes is provided below:

![Guess-Who-Characters-Summary](https://github.com/Lefteris-Souflas/Guess-Who-Best-Questions/assets/143879796/60a710dc-1e58-46d1-9ac5-aff3df44bd78)

## Initial Approach: Leveraging Oracle Data Mining

To expedite the process of identifying optimal strategies, the dataset was integrated into an **Oracle Database** using **SQL Developer**.

![Screenshot 2024-04-28 220634](https://github.com/Lefteris-Souflas/Guess-Who-Best-Questions/assets/143879796/3afc6074-92fe-4ea6-ac54-9a43cd94b6b7)

Employing **Oracle Data Mining (ODM)**, an attempt was made to leverage decision tree models. Guided by the instructions available on the [Oracle Help Center](https://docs.oracle.com/en/database/oracle/oracle-database/19/tutorial-apply-decision-tree/index.html), the following steps were undertaken:

- **Workflow Creation and Model Selection:**
  - Selected the Class Build node in the workflow.
  - Deselected all models except for the Decision Tree (DT) model.
  - Parameters of the Decision Tree were adjusted to foster the growth of a maximally informative tree.
  - Added a new Data Source node.
  - Selected the table GUESS_WHO.
  - Connected the GUESS_WHO node to the Class Build node.
  - Copied and pasted the GUESS_WHO node and renamed the node to GUESS_WHO_APPLY.
  - Added an Apply node.
  - Connected the Class Build node and the GUESS_WHO_APPLY node to the Apply node.

- **Model Execution:**
  - Ran the Apply node.
  - Checked for green check marks on all workflow nodes.

Regrettably, this approach failed to yield anticipated results, encountering a formidable challenge. Despite meticulous parameterization, an unresolved error surfaced, primarily attributed to the presence of unique values within the target variable. Consequently, an alternative avenue was pursued, invoking **Python Scikit-Learn** as the subsequent analytical framework.

![Screenshot 2024-05-11 142656](https://github.com/Lefteris-Souflas/The-Algorithmic-Way-of-Playing-Guess-Who/assets/143879796/70c1e22c-730a-4afa-a851-740eee5f2a20)

![Screenshot 2024-05-11 143348](https://github.com/Lefteris-Souflas/The-Algorithmic-Way-of-Playing-Guess-Who/assets/143879796/83f022ec-5d0d-43fb-94ac-1e3a29a02537)

![Screenshot 2024-05-11 143408](https://github.com/Lefteris-Souflas/The-Algorithmic-Way-of-Playing-Guess-Who/assets/143879796/dd952c06-9bb5-41db-887f-6eef4abeb00d)

![Screenshot 2024-05-11 143636](https://github.com/Lefteris-Souflas/The-Algorithmic-Way-of-Playing-Guess-Who/assets/143879796/570c597a-7597-4c18-bf0f-91de4a1c1d09)

![Screenshot 2024-05-11 143709](https://github.com/Lefteris-Souflas/The-Algorithmic-Way-of-Playing-Guess-Who/assets/143879796/7faa399b-c6d0-4f87-a28b-a462938c113b)

## Alternative Approach: Python Scikit-Learn

