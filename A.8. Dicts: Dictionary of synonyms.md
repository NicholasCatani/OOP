You are given a dictionary consisting of pairs of words. Every word is a synonym the other word in its pair. All the words in the dictionary are different.
First line of the input specifies how many word pairs will follow. After the dictionary, there is one more word given. Find a synonym for this word.

Input:
3
water liquid
fire heat
python java
fire

Output:
heat







################################################### Development

def synonym_dictionary():

    n = int(input(""))

    synonyms = {}

    for _ in range(n):
        word1, word2 = input("").split()
        synonyms[word1] = word2
        synonyms[word2] = word1

    word_to_find = input("")
    
    return synonyms.get(word_to_find, None)

print(synonym_dictionary())



