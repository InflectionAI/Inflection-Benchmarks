# MT-Bench Inf

In `mt_bench_inf.jsonl` we release a corrected version of the [MT-Bench](https://github.com/lm-sys/FastChat?tab=readme-ov-file#evaluation) questions that we use for evaluation. Each entry has the following fields:
* `question_id`: The question number
* `category`: Which MT-Bench category
* `turn`: A list with the turns
* `reference [optional]`: A reference answer

Below, we show a few examples of questions, the original GPT-4 Reference answer, and our corrected answer:

### Reasoning #104

Question:
```
David has three sisters. Each of them has one brother. How many brothers does David have?
```

GPT-4 Reference Answer:

```
David has only one brother.
```

Our Corrected Answer:

```
David has no brother. He is the one brother of his three sisters.
```

### Math #111

Question:

```
The vertices of a triangle are at points (0, 0), (-1, 1), and (3, 3). What is the area of the triangle?
```

GPT-4 Reference Answer:

```
To find the area of the triangle, we can use the formula for the area of a triangle with coordinates A(x1, y1), B(x2, y2), and C(x3, y3):
Area = (1/2) * |(x1(y2 - y3) + x2(y3 - y1) + x3(y1 - y2))|
In this case, the coordinates are A(0, 0), B(-1, 1), and C(3, 3). Plugging these values into the formula, we get:
Area = (1/2) * |(0(1 - 3) + (-1)(3 - 0) + 3(0 - 1))|
Area = (1/2) * |(-0 + 3 - 3)|
Area = (1/2) * |0|
Area = 0
The area of the triangle is 0. This means that the three points are collinear, and there is no triangle formed by these points.
```
Our Corrected Answer:
```
Area is 3
```
Overall, we find nearly 25% of examples in the reasoning, math, and coding categories had incorrect reference solutions or had flawed premises.

# Physics GRE

We release four processed Physics GRE exams, a common graduate school entrance exam for physics students.
* `physics_gre_scored.jsonl`: Exam GR8677 which we report results on.
* `physics_gre.jsonl`: Three aditional Physics GRE exams (GR9277, GR9677, and GR0177).
 Each entry has the following fields:
* `input`: The question
* `target_scores`: The correct answer choice
* `has_image`: Whether or not the question has an image. We include only questions without an image in our scoring.

| Model                 | Percentile |
| ----------------------| ---------: |
| Inflection-2.5 maj@8  | 85         |
| Inflection-2.5 maj@32 | 95         |
| GPT-4 maj@8           | 97         |


## Exam Scoring Details
For the Physics GRE, each correct answer is worth 1 point and each incorrect answer results in a -0.25 reduction. 
To compute score, we make the following assumption:
```
Raw_Score = Percentage_Correct - 0.25 * (1 - Percentage_Correct)
```
where `Percentage_Correct` is computed purely on questions without images. For simplicity, we do not use heuristics to allow the model not to answer.

| Raw Score    | Percentile |
| -----------: | ---------: |
| 81 &ndash; 100       | 98         |
| 77 &ndash; 80        | 97         |
| 75 &ndash; 76        | 96         |
| 72 &ndash; 74        | 95         |
| 71           | 94         |
| 69 &ndash; 70        | 93         |
| 67 &ndash; 68        | 92         |
| 65 &ndash; 66        | 91         |
| 64           | 90         |
| 63           | 89         |
| 61 &ndash; 62        | 87         |
| 60           | 86         |
| 59           | 85         |
| 57 &ndash; 58        | 84         |
| 56           | 82         |
| 55           | 80         |
| 53 &ndash; 54        | 78         |
| 52           | 77         |
| 51           | 75         |
| 49 &ndash; 50        | 72         |
| 48           | 70         |
| 47           | 69         |
| 45 &ndash; 46        | 66         |
| 44           | 64         |
| 43           | 62         |
| 41 &ndash; 42        | 59         |
| 40           | 57         |
| 39           | 54         |
| 37 &ndash; 38        | 52         |
| 36           | 48         |
| 35           | 46         |
| 33 &ndash; 34        | 43         |
| 32           | 41         |
| 30 &ndash; 31        | 38         |
| 29           | 35         |
| 28           | 32         |
| 26 &ndash; 27        | 30         |
| 25           | 27         |
| 24           | 25         |
| 22 &ndash; 23        | 22         |
| 21           | 20         |
| 20           | 18         |
| 18 &ndash; 19        | 16         |
| 17           | 14         |
| 16           | 12         |
| 14 &ndash; 15        | 10         |
| 13           | 9          |
| 12           | 8          |
| 10 &ndash; 11        | 6          |
| 9            | 5          |
| 8            | 4          |
| 6 &ndash; 7          | 3          |
| 5            | 2          |
| 1 &ndash; 4          | 1          |
| 0            | 0          |
