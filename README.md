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

## Alternative Approach: Employing Python Scikit-Learn

In lieu of the Oracle Data Mining (ODM) approach, **Python's Scikit-Learn** library was harnessed to delve into the intricacies of optimal strategy formulation for the "Guess Who?" game. The [implemented code](https://github.com/Lefteris-Souflas/The-Algorithmic-Approach-to-Winning-Guess-Who/blob/main/guess_who_code.ipynb) orchestrates a meticulously structured sequence of tasks encompassing data preparation, model training, feature importance analysis, and decision tree visualization. This holistic approach is tailored to enhance comprehension and strategic insight into effective gameplay tactics.

### Package Management and Environment Setup
To ensure streamlined management of Python package dependencies, the provided code block initiates with an endeavor to capture the current state of installed packages within the environment. This information is then preserved in a file named "freeze_file.txt", serving as a comprehensive record before proceeding with the installation of requisite packages specific to the Jupyter Notebook. The "requirements.txt" file specifies essential packages alongside their version numbers, facilitating seamless installation and alignment of the project environment with necessary dependencies.

### Data Preparation
The initial phase entails reading a dataset comprising all 24 characters of the game from a CSV file. This dataset encapsulates characters' English and Greek names in the first two columns, with subsequent columns representing binary responses (Yes/No) to various questions posed for each character.

Following dataset ingestion, segmentation into distinct entities is performed, delineating features (X) and the target variable (y).

### Decision Tree Modeling
#### Decision Tree Overview
Decision Trees, renowned for their versatility, represent a non-parametric supervised learning technique employed across classification and regression tasks. These models endeavor to construct a decision-making framework predicated on elementary decision rules deduced from dataset features, thereby facilitating prediction of the target variable. In our context, Decision Trees play a pivotal role in character identification within the "Guess Who?" game, employing a systematic questioning approach akin to gameplay mechanics.

#### Model Instantiation and Configuration
The Decision Tree Classifier instantiation involves meticulous configuration of various parameters governing model behavior and structure. Each parameter's value is meticulously chosen to optimize model efficacy and align with the inherent characteristics of the dataset. Key parameters include:

- **criterion**: Determines the impurity measure for node splitting, with 'gini' indicating Gini impurity.
- **splitter**: Dictates the strategy for selecting node splits, with 'best' opting for optimal splits.
- **max_depth**: Specifies the maximum depth of the decision tree.
- **min_samples_split**: Sets the minimum number of samples required to split an internal node.
- **min_samples_leaf**: Specifies the minimum number of samples required to be at a leaf node.
- **random_state**: Ensures reproducibility of results by fixing the random seed.

#### Model Training and Visualization
Following instantiation, the Decision Tree Classifier undergoes training on the dataset's features and classes. Post-training, the decision tree is visualized to elucidate the decision-making process underlying character identification. This visualization, facilitated by DOT data and the Graphviz library, offers a comprehensive depiction of decision pathways and criteria, enhancing strategic insight and gameplay efficacy.

![image](https://github.com/Lefteris-Souflas/The-Algorithmic-Approach-to-Winning-Guess-Who/assets/143879796/458de1e6-10cd-45d9-85f4-8845bb223ce3)

### Random Forest Modeling
#### Random Forest Overview
Random Forests, constituting an ensemble learning technique, excel in predictive accuracy and mitigate overfitting tendencies. Comprising a multitude of decision tree classifiers, Random Forests leverage averaging to enhance predictive efficacy.

#### Model Instantiation and Configuration
Similar to Decision Trees, Random Forest instantiation involves parameter configuration to tailor model behavior. Key parameters include:

- **n_estimators**: Specifies the number of decision trees in the forest.
- **max_depth**: Determines the maximum depth of each decision tree.
- **min_samples_split**: Sets the minimum number of samples required to split an internal node.
- **min_samples_leaf**: Specifies the minimum number of samples required to be at a leaf node.
- **random_state**: Ensures reproducibility of results.

#### Model Training and Feature Importance Analysis
Post-instantiation, the Random Forest Classifier undergoes training, followed by feature importance analysis to ascertain each feature's predictive significance. This analysis, depicted via bar plots, offers graphical representation of feature contributions, aiding strategic decision-making and gameplay optimization.

![image](https://github.com/Lefteris-Souflas/The-Algorithmic-Approach-to-Winning-Guess-Who/assets/143879796/0457ee22-c551-4d72-92db-3af5fee00d73)

![image](https://github.com/Lefteris-Souflas/The-Algorithmic-Approach-to-Winning-Guess-Who/assets/143879796/d64ecdb5-fb58-4847-b9e5-d48976670c41)

### Gradient Boosting Modeling
#### Gradient Boosting Overview
Gradient Boosting, leveraging boosting within a functional space, aims to minimize pseudo-residuals, yielding an ensemble model comprising weak learners, typically simplistic decision trees.

#### Model Instantiation and Configuration
Gradient Boosting instantiation entails parameter configuration to tailor model behavior. Key parameters include:

- **loss**: Specifies the loss function optimized during training.
- **learning_rate**: Determines the step size during gradient descent.
- **n_estimators**: Specifies the number of decision trees in the ensemble.
- **max_depth**: Determines the maximum depth of each decision tree.
- **random_state**: Ensures reproducibility of results.

#### Model Training and Feature Importance Analysis
Upon instantiation, the Gradient Boosting Classifier undergoes training, followed by feature importance analysis akin to previous models. This analysis facilitates identification of salient features crucial for predictive accuracy and strategic gameplay.

![image](https://github.com/Lefteris-Souflas/The-Algorithmic-Approach-to-Winning-Guess-Who/assets/143879796/a759bb96-d597-4fcc-9f82-d03609c34fc6)

![image](https://github.com/Lefteris-Souflas/The-Algorithmic-Approach-to-Winning-Guess-Who/assets/143879796/ff54159b-a8d4-455c-bfc8-685447e97dc3)

### LightGBM Modeling
#### LightGBM Overview
LightGBM, a gradient boosting framework, boasts accelerated training speed, reduced memory consumption, and enhanced accuracy. It represents an ideal choice for large-scale datasets and complex predictive modeling tasks.

#### Model Instantiation and Configuration
LightGBM instantiation involves parameter configuration, aligning model behavior with dataset characteristics. Key parameters include:

- **boosting_type**: Specifies the boosting algorithm employed.
- **num_leaves**: Sets the maximum number of leaves in each tree.
- **learning_rate**: Determines the step size during gradient descent.
- **n_estimators**: Specifies the number of boosting rounds.
- **random_state**: Ensures reproducibility of results.

#### Model Training and Feature Importance Analysis
Post-instantiation, the LightGBM Classifier undergoes training, followed by feature importance analysis akin to previous models. This analysis facilitates identification of salient features crucial for predictive accuracy and strategic gameplay.

![image](https://github.com/Lefteris-Souflas/The-Algorithmic-Approach-to-Winning-Guess-Who/assets/143879796/6f9bde5d-fa8d-4f90-84be-10b03b48c686)

![image](https://github.com/Lefteris-Souflas/The-Algorithmic-Approach-to-Winning-Guess-Who/assets/143879796/f7c6916c-0c86-4e44-956e-f3f3fc7e26de)

### Model Summary and Character Identification
The performance and efficacy of each model are summarized based on the minimum and maximum number of questions required for character identification. This summary aids in selecting the optimal model for efficient gameplay and strategic advantage.

| Models | Min # Questions | Max # Questions |
| :---   |  ---: |       ---: |
| 1. GradientBoostingClassifier | 3 | 6 |
| 2. LGBMClassifier | 3 | 7 |
| 3. RandomForestClassifier | 3 | 8 |
| 4. DecisionTreeClassifier | 3 | 8 |

The results of the models implemented above can be reproduced by running the [Jupyter Notebook](https://github.com/Lefteris-Souflas/The-Algorithmic-Approach-to-Winning-Guess-Who/blob/main/guess_who_code.ipynb).

