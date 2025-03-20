# Decision Tree Classifier

## Project Description
This project implements a custom Decision Tree Classifier from scratch in Python. The implementation focuses on handling continuous numerical attributes and includes mechanisms for dealing with missing values. The decision tree is built using information gain and entropy calculations to make optimal splits in the data.

## Features
- Custom implementation of a binary decision tree classifier
- Handles continuous numerical attributes
- Supports missing value handling
- Information gain-based splitting criteria
- Entropy-based node evaluation
- Configurable minimum leaf size
- Built-in train-test split functionality
- Support for probability estimates at leaf nodes

## Project Structure
- `decision_tree.py`: Main implementation of the decision tree algorithm
- `basic_tree_data.csv`: Sample dataset for testing the classifier
- `mass_towns_2022.csv`: Additional dataset for real-world application

## Implementation Details
The decision tree implementation includes several key components:
- `DecisionTree`: Main class that builds and manages the tree structure
- `DecisionNode`: Internal nodes that perform binary splits on attributes
- `LeafNode`: Terminal nodes that store class predictions and probabilities
- Helper functions for:
  - Data reading and preprocessing
  - Entropy calculation
  - Information gain computation
  - Best split finding
  - Train-test splitting

## Usage
To use the decision tree classifier:

```python
# Read the data
examples = read_data('your_data.csv')

# Split into train and test sets
train_data, test_data = train_test_split(examples, test_perc=0.2)

# Create and train the model
dt = DecisionTree(
    examples=train_data,
    id_name='id',  # Name of identifier column
    class_name='cls',  # Name of class label column
    min_leaf_count=1  # Minimum examples required at leaf nodes
)

# Classify new examples
for example in test_data:
    prediction, probability = dt.classify(example)
```

## Data Format
The classifier expects data in CSV format with:
- A unique identifier column
- A class label column
- One or more numerical attribute columns
- Support for missing values (empty cells in CSV)

## Requirements
- Python 3.x
- Standard Python libraries:
  - csv
  - random
  - math

No external dependencies are required as this is a pure Python implementation.

## Performance Considerations
- The tree building process uses recursive partitioning
- Split evaluation considers all possible threshold values for numerical attributes
- Memory usage scales with the number of examples and attributes
- Prediction time is logarithmic in the depth of the tree 