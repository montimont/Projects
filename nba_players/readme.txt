## Sample Player Inference

In this final step, we test the trained neural network by feeding it a sample player's profile. The player has:

- Age: 26  
- Height: 200 cm  
- Weight: 95 kg  
- Games Played: 70  
- Rebounds per game: 6.0  
- Assists per game: 5.0  
- Net Rating: 5.5  
- Offensive Rebound %: 3.0%  
- Defensive Rebound %: 15.0%  
- Usage Rate: 22.0%  
- True Shooting %: 58.0%  
- Assist Rate: 20.0%

These features are scaled and passed into the model, which outputs the predicted number of points per game.

This allows us to evaluate model performance on real-like test cases and demonstrates its capability to support hypothetical player evaluations and scouting insights.
