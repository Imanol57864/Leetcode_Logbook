# 49. Group Anagrams

- https://leetcode.com/problems/group-anagrams/description/

## My solution
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        # Group the strings based on containing the same universe of characters
        # Check if the characterBag already exists
            # If not, create a new list and append that value
            # If yes, sort it out to append it to the correct list

        # Get the logical key of a word
        def getLogicalKey(string: str):
            if not string:
                return "" # Its not false, is empty string
            x = sorted(string) # Create a list of sorted chars
            key = "".join(x) # Join back the list
            return key

        # Dictionary to track each logical universe
        universes = {}
        
        # For each item, get its logical key, and track it
        for item in strs:
            key = getLogicalKey(item)
            if key != False:
                if key in universes.keys():
                    universes[key].append(item) # append to already created list
                else:
                    universes[key] = [item] # create a new list to its logical key
                    
        # Lastly, get a list of its values
        # {'aet': ['eat', 'tea', 'ate'], 'ant': ['tan', 'nat'], 'abt': ['bat']}
        res = list(universes.values())
        return res
```

## Notes
- Key: https://www.youtube.com/watch?v=RcZsTI5h0kg
- Basically logical key + dictarionaries and "list()" func