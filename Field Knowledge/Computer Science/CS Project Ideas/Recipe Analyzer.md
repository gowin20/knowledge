# Recipe Analyzer

Finds websites to analyze

- 

Reads in webpages from recipe sites

- dynamically looks for an "ingredients" subheading and reads in the ingredients
- stores the recipe + ingredients in a JSON file

Makes a "food" node for each food listed as an ingredient

- Food nodes store information about how frequently food is used
- also stores info about what ingredients they are commonly used with.
    - Ordered dictionary, with entries formatted foodnode:frequency .
    - possible to recursively search this web of food in order to generate recipes dynamically