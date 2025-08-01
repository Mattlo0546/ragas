# Evaluate a JSON dataset with Ragas

This guide shows how to load a JSON file with question--answer pairs and evaluate it using Ragas metrics. You can [open the notebook in Google Colab](https://colab.research.google.com/github/explodinggradients/ragas/blob/main/docs/howtos/applications/evaluate_json_dataset.ipynb).

## Steps

1. Install `ragas` and `datasets` libraries.
2. Load your dataset from the JSON file.
3. Create an `EvaluationDataset` from the loaded data.
4. Run `ragas.evaluate()` with the metrics you want.

```python
!pip install ragas datasets

import json
from ragas import EvaluationDataset, evaluate
from ragas.metrics import AnswerRelevancy, Faithfulness

with open("../_static/simple_eval_dataset.json") as f:
    data = json.load(f)

dataset = EvaluationDataset.from_list(data)
result = evaluate(dataset, metrics=[AnswerRelevancy(), Faithfulness()])
print(result)
```
