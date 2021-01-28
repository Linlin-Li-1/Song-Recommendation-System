# Song-Recommendation-System
The song recommendation system is based on the user's workout plan and previous listening history on Spotify. Ideally, users will be able to design and submit their exercise plan, including the duration and sequence of each exercise intensity, the machine will output a new playlist containing song recommendations, and users can directly play and enjoy these songs during the exercise. And the energy curve of these songs is consistent with the user's exercise intensity. For example, they will hear energetic songs during intense aerobic exercise and smooth songs during warm-up and end.

### Phase 1
#### Goal
Given a playlist or a list of songs and the user's listening history, the machine can generate a list of song recommendations that should maintain the "energy curve" (we only consider the direction of the trend) for workout purposes and and the generated playlist should be similar to the target as close as possible. To reduce the deviation between the original playlist and the recommended playlist, "Meet Middle" method was proposed and implemented. 

#### Methods
There are a total of four proposed methods:

- **Pure method**: <u> Submit queries to Spotify Get Recommendations API and get a list of recommendations for each song in the target playlist, and then filter these recommendations according to the trend of energy.</u> 

- **Meet-middle method**: Since the Pure method starts from the first song, the difference between the target plalylist and the list of recommended songs will enlarge as the number of songs increases. To alleviate this issue, I proposed the **Meet-middle method**. 
<div align=center><img width="550px" src="meetmiddle.png"/></div>

- **Recommend first, then place common songs**: <u>Use a **modified version of Pure method** to generate a list of recommendations. Then replace some recommendations by common songs. </u> 

- **Place common songs first, then recommend**:<u> Compare the "difference" between each target song and each common song and determine the places for some common songs. Then use **Meet-middle method** to generate recommendations between common songs. 

### Phase 2
#### Goal
Given the workout plan of the user, the machine can generate a playlist using top songs or recently played songs. Combine phase 1 and 2, first use phase 2's method to generate a "target" playlist and then use phase 1's methods to customize the recommendations.

### Phase 3
#### Goal
Apply machine learning methods to learn and customize the parameter weights, and provide personalized recommendations for each user.
