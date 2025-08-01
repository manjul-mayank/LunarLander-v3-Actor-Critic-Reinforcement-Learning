# 🚀 LunarLander-v3: Actor-Critic Reinforcement Learning

A deep reinforcement learning project using the Actor-Critic method to train a lander to safely land on a rugged terrain — powered by OpenAI Gymnasium and TensorFlow.

## 🎯 Project Goal

To build an intelligent agent that learns to land a lunar module on various terrains using continuous feedback, policy optimization, and reward shaping.

---

## 🌌 Overview

The environment is highly stochastic. Each episode starts with a randomized terrain, and the lander uses its engines (main and side boosters) to guide itself to a flat landing. Success is defined by:

- Smooth touchdown
- Proper orientation
- Staying within velocity and angle thresholds

We've implemented:
- Advantage Actor-Critic (A2C) architecture
- Generalized Advantage Estimation (GAE)
- Entropy regularization
- Custom success/failure/neutral evaluation logic
- Video recording of successful landings

---

## 🧠 Algorithm: Advantage Actor-Critic (A2C)

A hybrid between:
- **Actor**: Outputs a probability distribution over actions
- **Critic**: Estimates the value of states

We use:
- A shared backbone network
- Exponential LR decay
- Entropy bonus to encourage exploration
- Gradient clipping for stability

---

## 📊 Results & Observations

- The terrain randomness makes this a probabilistic learning task.
- The lander is guided only by reward feedback — there is no explicit planning.
- Each failure leads to a different approach in the next episode, demonstrating **emergent exploration**.
- The success rate is **non-deterministic** due to infinite landing possibilities.

### 🟢 Success
> Lander achieves all landing criteria.

### 🔴 Failure
> Crashes or flips over before touchdown.

### ⚪ Neutral
> Not clearly a success or failure — either sub-optimal landing or reward within a buffer zone.

---

## 🎥 Demo

![Landing Demo](lunar_ep1.mp4)

➡️ Check out `/videos` for full rendering of trained policy.

---

## 🛠️ Installation

```bash
pip install -r requirements.txt

Requirements:

Python 3.10+

TensorFlow 2.15+

gymnasium[box2d]

matplotlib

tqdm

imageio
```
## ✅ Where This Performs Well
- On moderately randomized terrain

- When consistent reward shaping is maintained

- When trained for >500 episodes with entropy decay

## ❌ Where It May Struggle
- Extremely steep or narrow terrain zones

- Short episode lengths (due to early termination)

- Lack of memory or planning (non-recurrent policy)
## 📌 Key Takeaway
This is a probabilistic control problem, and our A2C agent learns through trial and error, using policy gradients and temporal rewards. The environment’s variability means that the agent doesn't converge to a single deterministic policy — instead, it generalizes over countless landing strategies.
## 🧠 Future Work
- Add recurrent layers (LSTM) for temporal memory

- Try PPO or TRPO for better performance

- Incorporate curriculum learning or terrain shaping
## 🤝 Contributing
Pull requests welcome! For major changes, open an issue first to discuss.
## 📜 License
MIT License
## Author
- Manjul Mayank
