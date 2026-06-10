import random
text_data = """
The quick brown fox jumps over the lazy dog. 
The lazy dog sleeps all day under the warm sun. 
The quick brown fox is always looking for an adventure in the forest.
"""

# Clean and tokenize the text into individual words
words = text_data.lower().split()

# This dictionary will store a word as a 'Key' and all possible next words as 'Values'
markov_chain = {}

for i in range(len(words) - 1):
    current_word = words[i]
    next_word = words[i + 1]
    
    # If the word is not in the dictionary, add it
    if current_word not in markov_chain:
        markov_chain[current_word] = []
        
    # Append the next word to the list of transitions
    markov_chain[current_word].append(next_word)

print("Markov Chain Dictionary built successfully!")
print("Transitions for 'the':", markov_chain.get('the'))


def generate_text(chain, start_word, limit=15):
    word = start_word.lower()
    sentence = [word]
    
    for _ in range(limit - 1):
        # Check if the current word has any known next words
        if word in chain:
            # Randomly pick the next word based on the stored possibilities
            next_word = random.choice(chain[word])
            sentence.append(next_word)
            word = next_word  # Move to the next word
        else:
            break # Stop if a word has no following transitions
            
    return " ".join(sentence)

# Pick a starting word present in your dataset
starting_word = "the"
generated_output = generate_text(markov_chain, start_word=starting_word, limit=12)

print("\n--- Final Generated Output ---")
print(generated_output)

The Output image:
w<img width="815" height="137" alt="Screenshot 2026-06-10 221907" src="https://github.com/user-attachments/assets/d0763404-23f7-4bb9-bd29-58cbbb8a3ffc" />
