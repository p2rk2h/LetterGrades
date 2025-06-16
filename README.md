# LetterGrades
LetterGrades Class for manipulating list of standard LetterGrades to calculate mean, median, etc.


A) LetterGrade class requirements:

1) Map standard letter grades to GPA digits:
   (A+, A, A-) = (4.25, 4.0, 3.75),
   (B+, B, B-) = (3.25, 3.0, 2.75),
   (C+, C, C-) = (2.25, 2.0, 1.75),
   (D+, D, D-, F) = (1.25, 1.0, 0.75, 0.0).

3) Map digits in [0, 4.25] to the nearest single grade (e.g., 4.0 → A) or a composite of two grades (e.g., 3.625 → A/B+, as (4.0 + 3.25)/2 = 3.625), listing the higher grade first in composites.
   For ties between composites (e.g., 3.5 as A/B = 3.5 or A-/B+ = 3.5), select the composite with the narrowest gap.
   Limit composites to two grades, separated by a slash.

5) Support arithmetic operations (+ and -) with numbers or LetterGrade instances, clamping results to the range, [0, 4.25].

6) Implement dot products between a list of weights (floats) and a list of LetterGrade objects, returning a LetterGrade if in [0, 4.25], else a float.

7) For a list of LetterGrade objects, compute the numeric median and return the nearest single or composite grade, plus provide five L1 tuples for minimum, Q1, median, Q3, and maximum.

8) For interquartile Q1 and Q3 calculation, use flags 'ii': to include median in both halves (e.g., [2.0, 3.0, 3.25, 3.75, 4.25] → lower [2.0, 3.0, 3.25], upper [3.25, 3.75, 4.25]).  For even list length, both halves contain all items.
  'ee': to exclude median from both (e.g., lower [2.0, 3.0], upper [3.75, 4.25]).  Default in deference to Tukey's preference.
  'ie': to include in lower, exclude from upper (e.g., lower [2.0, 3.0, 3.25], upper [3.75, 4.25]). 


B) Some tough test cases to pass:

1) assert LetterGrade('3.4375').to_letter( ) == 'A-/B+'

2) assert LetterGrade('3.5675').to_letter( ) == 'A-/B+'

3) w , g = [0.6, 0.3, 0.1] , ['A-/B+', 'A-/B+', 'A+']    
   assert LetterGrade.dot_product( w , g ).to_letter( ) == 'A-/B+'
