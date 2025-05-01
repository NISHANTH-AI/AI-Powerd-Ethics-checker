# AI-Powerd-Ethics-checker
AI-powered Ethics Checker that evaluates content for ethical issues such as bias, discrimination, misinformation, and harmful language. Ensures content adheres to ethical standards and promotes responsible communication.
from transformers import pipeline
# Load the model
explainer = pipeline("text2text-generation", model="google/flan-t5-base")
# Banned / unethical terms
banned_words = [
"drugs", "weapon", "scam", "blackmail", "steal", "threat", "kill", "deepfake",
"hack", "illegal", "terror", "harass", "discriminate", "racist",
judge people by", "skin color", "violence", "spy"
ef check_project_ethics(project_description):
project_lower = project_description. lower ()
# Rule-based unethical check
if any(word in project_lower for word in banned_words):
return (
"X Not Ethical",
"This project contains Illegal, harmful, or discriminatory elements.",
"Suggestion: Focus on solving positive challenges in AI like education, healthcare, or accessibility."
# Model-based reasoning
prompt = (
f"Is the following AI project ethical? If not, say why.
f"If yes, give suggestions to improve it responsibly:\n{project_description]"
response = explainer(prompt, max_length=100, do_sample=False) [0] ['generated_text'].strip()
lower_response = response. lower()
# Basic logic for verdict
if "not ethical" in lower_response or "unethical" in lower_response or "illegal" in lower_response:
verdict = "X Not Ethical"
elif "ethical" in lower_response and "not" not in lower_response:
verdict = " Ethical"
elif lower_response in ["yes", "maybe", "okay", "idk"]: # Too vague
verdict = " Ethical (Assumed)"
response = "This seems like a safe and helpful project. Ensure transparency, use content moderation best practices, and avoid false positives."
else:
verdict = "A Unclear - Needs Human Review"
return verdict, response, "Suggestion: Improve user transparency, avoid bias, and ensure fairness."
# Input
print("Describe your AI project:")
user_input = input(" ")
# Run ethics check
verdict, explanation, suggestion = check_project_ethics(user_input)
# Output
print("\nEthics Check Result: )
print(f"Verdict: {verdict}")
print(+"Explanation: {explanation}")
print(+"{suggestion}")

