# AI-Powerd-Ethics-checker
AI-powered Ethics Checker that evaluates content for ethical issues such as bias, discrimination, misinformation, and harmful language. Ensures content adheres to ethical standards and promotes responsible communication.
!pip install flask pyngrok
# Basic AI Project Ethical Checker in Python

# List of unethical or risky keywords
banned_keywords = [
    "drugs", "weapon", "scam", "blackmail", "steal", "threat", "kill", "deepfake",
    "hack", "illegal", "terror", "harass", "discriminate", "racist",
    "judge people by", "skin color", "violence", "spy", "surveillance"
]

def check_ai_project_ethics(description):
    desc_lower = description.lower()

    # Step 1: Rule-based keyword check
    flagged = [word for word in banned_keywords if word in desc_lower]

    # Step 2: Verdict logic
    if flagged:
        verdict = "❌ Not Ethical"
        explanation = f"This project includes unethical terms like: {', '.join(flagged)}"
        suggestion = "Focus on solving positive problems in education, health, or environment."
    elif "bias" in desc_lower or "fake" in desc_lower:
        verdict = "⚠️ Needs Human Review"
        explanation = "Potential concerns found. Review for bias or misinformation."
        suggestion = "Ensure fairness, accuracy, and transparency."
    else:
        verdict = "✅ Ethical"
        explanation = "No unethical patterns found."
        suggestion = "Still follow AI safety, fairness, and privacy guidelines."

    return verdict, explanation, suggestion

# Example Usage
if __name__ == "__main__":
    print("Enter your AI project description:")
    user_input = input(">> ")
    verdict, explanation, suggestion = check_ai_project_ethics(user_input)
    print("\n--- Ethics Check Result ---")
    print("Verdict     :", verdict)
    print("Explanation :", explanation)
    print("Suggestion  :", suggestion)
