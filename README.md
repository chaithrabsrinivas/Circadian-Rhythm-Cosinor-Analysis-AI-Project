# Circadian-Rhythm-Cosinor-Analysis-AI-Project

# ⏰ Circadian Rhythm & Cosinor Analyzer (Physics-Informed Neural Network)

health AI project that reconstructs a person's full **24-hour body clock (circadian rhythm)** from just **6 noisy smartwatch readings**—and automatically calculates key clinical Cosinor health metrics.

## 🌟 What This Project Does
Smartwatches and hospital monitors often record messy, incomplete data with gaps throughout the day. Instead of needing continuous measurements, this project uses a **Physics-Informed Neural Network (PINN)** to combine basic machine learning with natural biological wave rules:

1. **The Smartwatch Check:** The AI matches the 6 actual temperature readings collected during the day.
2. **The 24-Hour Body Clock Rule:** Human body temperature naturally rises and falls in a smooth 24-hour wave (a cosine rhythm). The AI enforces this biological pattern across all 24 hours to fill in missing gaps accurately.

### 📊 Clinical Cosinor Metrics Calculated
Once the 24-hour curve is rebuilt, the script automatically prints a health report containing:
* **MESOR (Daily Average):** The baseline body temperature across the entire day (~36.8°C).
* **Amplitude (Rhythm Strength):** How strongly the body swings between day and night (±0.4°C). A flattened swing can signal fatigue or sleep disruption.
* **Acrophase (Peak Time):** The exact hour when body temperature reaches its daily high (~4:00 PM / 16:00).

## 🛠️ Tech Stack
* **Python 3.8+**
* **PyTorch** (for the neural network and automatic wave tracking)
* **NumPy** (for extracting Cosinor rhythm metrics)
* **Matplotlib** (for plotting the 24-hour circadian wave)

## 🚀 How to Run the Project

### 1. Install Dependencies
Open your terminal or command prompt and run:
```bash
pip install torch numpy matplotlib
```

### 2. Run the Script
Execute the Python file:
```bash
python circadian_pinn.py
```

### 3. View the Output
After ~6 seconds of training (3,000 steps), you will see:
* **Terminal Report:** A printed summary comparing the AI's estimated MESOR, Amplitude, and Peak Time against the true values.
* **Visual Graph:** A 24-hour chart showing how the AI connects **6 scattered red dots** (smartwatch readings) into a smooth **green dashed circadian wave**.

## 🧪 Experiment Ideas
You can test different health and lifestyle scenarios by editing the variables at the top of `circadian_pinn.py`:
* **Model Daily Heart Rate:** Change `TRUE_MESOR = 72.0` (bpm), `TRUE_AMPLITUDE = 12.0` (bpm), and `estimated_mesor = nn.Parameter(torch.tensor([70.0]))` to track heart rate instead of temperature.
* **Simulate Jet Lag or Night-Shift Work:** Change `TRUE_PEAK_HOUR = 16.0` to `4.0` (4:00 AM) to see how shift work flips a person's internal body clock.

