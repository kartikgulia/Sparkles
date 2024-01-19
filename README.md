# Sparkles
Lava Lamp Secure Key Password

Initial Algorithim Idea:
**(Secure because it captures and ecodes position and movement of lava lamps) **
— know exact functions to use/ little experience
Take 6 pictures spaced over X seconds —> Grey scale images(opencv) —> Compute transition change frames(1->2, 3->4, 5->6) between pictures(opencv absdiff()) —> Compute transition changes from transition frames( 12->34, 34->56)

**(“Messing up” data portion - multiple ways to do this but it should be hidden) — previous done**
SVD (approximate matrix) - Do for both transition transition frame. Using vT from now on.

**(Funneling data and adding uncertainty) — previous done**
Reservoir Sampling(n=30) - of both transition frames, vT, to get uniform sample of transition frame
Normalize the samples with min and max to be 0 and 179

**(Picking Characters)**
Given string, called character_list with all potential characters (a-z, A-Z, 0-9, !@#$%^&()+){}<>?|=[]\;/ or 85 characters to chose from)
For each position in 15 character output, set output[i] = character_list[normalized_sampled[i] + normalized_sampled[i+15])%85]
