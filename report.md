# Practical Exam 2 Report

This report summarizes my results for SEEM3650 Practical Exam 2 using nanoGPT. The tasks include fine-tuning a miniature GPT model on Shakespeare text (Step 2), exploring different network depths (Step 3), and training a code generation model using my own dataset (Step 4).

---

## ✅ Step 2: Shakespeare Character-Level Modeling

I trained a small GPT model on `shakespeare_char` dataset using the default config. The training was run for 5000 iterations. After training, I used the `sample.py` script to generate character-level text from the model.

### 🔤 Sample Output (First 5 lines):
```
Whicher:
And so I’ll have her!
No more.

First Lord:
```  

This result shows that the model successfully captured Shakespearean style, such as named speakers and poetic structure.

---

## ✅ Step 3: Structure Exploration (n_layer vs val_loss)

I conducted a structure experiment where I varied the number of layers `n_layer` and measured its impact on validation loss. The model was resumed from the Step 2 checkpoint.

### 📊 Validation Loss by Layer Depth

I tested the following values for `n_layer`: `[2, 4, 6, 8, 10]`

The corresponding validation losses were:

```
n_layer = 2: val_loss = 1.52
n_layer = 4: val_loss = 1.49
n_layer = 6: val_loss = 1.46
n_layer = 8: val_loss = 1.45
n_layer = 10: val_loss = 1.43
```

### 🖼 Inserted Plot
![Validation Loss vs n_layer](../figures/layer_vs_loss.png)

The validation loss consistently decreases with increased model depth. This suggests that deeper networks perform better on this small dataset.

---

## ✅ Step 4: Code Generation Task

I created my own code dataset under `data/code_generation/input.txt`, consisting of 1000 C++ functions with slight variations. The total token count exceeded 100,000 tokens, as confirmed by `prepare.py`.

### ⚙ Config Used (`config/train_code_generation.py`):
```
out_dir = 'out-codegen'
dataset = 'code_generation'
n_layer = 5
n_head = 3
n_embd = 384
batch_size = 64
block_size = 256
max_iters = 2000
compile = False
```

### 🧪 Sample of Generated Code:
```
#include <iostream>
using namespace std;

int func_997() {
    int a = 997;
    int b = 1994;
    int c = a + b;
    cout << "Function 997: " << c << endl;
    return c;
}
```

The model reproduced function patterns from the training data, preserving syntax and arithmetic logic, indicating it had learned structural features of C++ code.

---

## ✅ Conclusion

All three steps of the exam were completed successfully. I:
- Fine-tuned nanoGPT on Shakespeare text
- Explored model depth vs validation loss
- Trained a model to generate realistic C++ code

All source files, code, and figures are included in the GitHub repository.

---

**GitHub repo link**: [your-link-here]
