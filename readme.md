
## App Project - Score Keeper for Pingpong

### 1. Rules
Score
A player receives 1 point every time when legitmately serves or hits ball and the opponent fails to hit ball back without any foul.

Foul
A player loses 1 point to the opponent every time when serves or hits ball illegimiately, i.e. foul.

Win
There are 7 rounds in one game.

In each round, if a player first gets 11 points when the other is below 10 points or 2 points ahead of the opponent when both have 10 or more points, he or she wins this round.

The player who first wins 4 rounds wins the whole game.

### 2. How My App Looks
The app I made includes two main activities:

- Score tracker: show the scores and rounds.

<img src = "images/1.png" style="width:200px; height:350px" >

- Result: show the statistics of scores and fouls of the whole game.

<img src = "images/2.png" style="width:200px; height:350px" >

### 3. How My App Works
#### Score Tracker
- SCORE and FOUL

For example, when player A scores, click “SCORE” below “Player A” to add 1 point for player A:

<img src = "images/3.png" style="width:200px; height:350px" >

When player A fouls, click “FOUL” below “Player A” to add 1 point for player B (we don’t click “SCORE” below “Player B” in this case, because we want to keep track of fouls for analysis after the game):

<img src = "images/4.png" style="width:200px; height:350px" >

- NEXT ROUND

When one player reaches 11 points and at least 2 points ahead of the other player, the round is over. In this case, if we still hit SCORE or FOUL, the app will remind us to “Click Next Round” on the top of the screen:

<img src = "images/5.png" style="width:200px; height:350px" >
<img src = "images/11.png" style="width:200px; height:350px" >

If we hit “NEXT ROUND” before the round is over, the app will give another hint “This round is not over”:

<img src = "images/6.png" style="width:200px; height:350px" >

When “NEXT ROUND” works, the individual scores for player A and B will be cleared to 0, and the total scores are calculated and shown on top of the screen. For example, the screen below shows “2-0” between player A and B:

<img src = "images/7.png" style="width:200px; height:350px" >

When a player has already won 4 rounds and we click “Next Round” or click “SCORE”, “FOUL” OR “NEXT ROUND”, the app will tell us “Player has won!”, which means the game is over:

<img src = "images/12.png" style="width:200px; height:350px" >

- Check Result

When the game is over, we can check the result for a better understanding of the whole game, such as who scores more and who makes more fouls during the game:


<img src = "images/10.png" style="width:200px; height:350px" > 

- Reset

When we want to start over, just click “RESET”, and all the scores and statistics will be cleared and reset to 0.

### 4. Video
I made a video to demonstrate how the app works:

https://www.youtube.com/watch?v=AevC0y4J378

### 5. Original Code

There are two activities in this app: activity_main.xml and activity_display_result.xml.

- activity_main.xml   

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/vs_score"
        android:layout_width="wrap_content"
        android:layout_height="32dp"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="8dp"
        android:text="0 - 0"
        android:textColor="@android:color/holo_blue_dark"
        android:textSize="24sp" />

    <LinearLayout
        android:id="@+id/score_panel"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="48dp"
        android:orientation="horizontal">

        <LinearLayout
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:orientation="vertical">

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginBottom="16dp"
                android:gravity="center"
                android:padding="4dp"
                android:text="Player A"
                android:textColorLink="#616161"
                android:textSize="18sp" />

            <TextView
                android:id="@+id/player_a_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginBottom="24dp"
                android:fontFamily="sans-serif-light"
                android:gravity="center"
                android:padding="4dp"
                android:text="0"
                android:textColorLink="#000000"
                android:textSize="56sp" />

            <Button
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginBottom="8dp"
                android:layout_marginLeft="24dp"
                android:layout_marginRight="24dp"
                android:onClick="addOneForPlayerA"
                android:text="Score" />

            <Button
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginBottom="8dp"
                android:layout_marginLeft="24dp"
                android:layout_marginRight="24dp"
                android:onClick="loseOneToPlayerB"
                android:text="FOUL" />


        </LinearLayout>

        <LinearLayout

            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:orientation="vertical">

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginBottom="16dp"
                android:gravity="center"
                android:padding="4dp"
                android:text="Player B"
                android:textColorLink="#616161"
                android:textSize="18sp" />

            <TextView
                android:id="@+id/player_b_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginBottom="24dp"
                android:fontFamily="sans-serif-light"
                android:gravity="center"
                android:padding="4dp"
                android:text="0"
                android:textColorLink="#000000"
                android:textSize="56sp" />

            <Button
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginBottom="8dp"
                android:layout_marginLeft="24dp"
                android:layout_marginRight="24dp"
                android:onClick="addOneForPlayerB"
                android:text="Score" />

            <Button
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginBottom="8dp"
                android:layout_marginLeft="24dp"
                android:layout_marginRight="24dp"
                android:onClick="lostOneToPlayerA"
                android:text="Foul" />


        </LinearLayout>
    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="180dp"
        android:layout_alignBottom="@id/score_panel"
        android:layout_alignParentBottom="true"
        android:layout_gravity="center"
        android:orientation="vertical">


        <Button
            android:id="@+id/next_round"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginBottom="12dp"
            android:layout_marginLeft="110dp"
            android:layout_marginRight="110dp"
            android:onClick="nextRound"
            android:text="Next Round"
            android:textSize="14sp" />

        <Button
            android:id="@+id/check_result"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginBottom="12dp"
            android:layout_marginLeft="110dp"
            android:layout_marginRight="110dp"
            android:onClick="showResult"
            android:text="CHECK RESULT"
            android:textSize="14sp" />

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginLeft="110dp"
            android:layout_marginRight="110dp"
            android:onClick="resetScore"
            android:text="RESET"
            android:textSize="14sp" />

    </LinearLayout>

    <View
        android:layout_width="1dp"
        android:layout_height="320dp"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="54dp"
        android:background="@android:color/darker_gray" />

</RelativeLayout>

```


- MainActivity.java


```java
package com.example.android.scorekeeperpingpong;

import android.content.Intent;
import android.os.Bundle;
import android.support.v7.app.AppCompatActivity;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }


    int scorePlayerA = 0;
    int scorePlayerB = 0;
    int foulPlayerA = 0;
    int foulPlayerB = 0;

    int total_a = 0;
    int total_b = 0;

    int round_n = 1;

    /**
     * Increase the score for A by 1 point.
     */
    public void addOneForPlayerA(View v) {
        if ((total_a < 4 && total_b < 4) && ((scorePlayerA >= 11 && scorePlayerA - scorePlayerB >= 2) || (scorePlayerB >= 11 && scorePlayerB - scorePlayerA >= 2))) {
            displayForVersus("Please click \"Next Round\"");
        } else if (total_a == 4) {
            displayForVersus("Player A has won the game!");
        } else if (total_b == 4) {
            displayForVersus("Player B has won the game!");
        } else {
            scorePlayerA = scorePlayerA + 1;
            displayForPlayerA(scorePlayerA);
            if (scorePlayerA >= 11 && scorePlayerA - scorePlayerB >= 2) {
                displayForVersus("Player A has won this round");
            }
        }
    }

    /**
     * Lost one score to B if foul.
     */
    public void loseOneToPlayerB(View v) {
        if ((total_a < 4 && total_b < 4) && ((scorePlayerA >= 11 && scorePlayerA - scorePlayerB >= 2) || (scorePlayerB >= 11 && scorePlayerB - scorePlayerA >= 2))) {
            displayForVersus("Please click \"Next Round\"");
        } else if (total_a == 4) {
            displayForVersus("Player A has won the game!");
        } else if (total_b == 4) {
            displayForVersus("Player B has won the game!");
        } else {
            scorePlayerB = scorePlayerB + 1;
            displayForPlayerB(scorePlayerB);
            foulPlayerA = foulPlayerA + 1;
            if (scorePlayerB >= 11 && scorePlayerB - scorePlayerA >= 2) {
                displayForVersus("Player B has won this round");
            }
        }
    }

    /**
     * Increase the score for B by 1 point.
     */
    public void addOneForPlayerB(View v) {
        if ((total_a < 4 && total_b < 4) && ((scorePlayerA >= 11 && scorePlayerA - scorePlayerB >= 2) || (scorePlayerB >= 11 && scorePlayerB - scorePlayerA >= 2))) {
            displayForVersus("Please click \"Next Round\"");
        } else if (total_a == 4) {
            displayForVersus("Player A has won the game!");
        } else if (total_b == 4) {
            displayForVersus("Player B has won the game!");
        } else {
            scorePlayerB = scorePlayerB + 1;
            displayForPlayerB(scorePlayerB);
            if (scorePlayerB >= 11 && scorePlayerB - scorePlayerA >= 2) {
                displayForVersus("Player B has won this round");
            }
        }
    }

    /**
     * Lost one score to B if foul.
     */
    public void lostOneToPlayerA(View v) {
        if ((total_a < 4 && total_b < 4) && ((scorePlayerA >= 11 && scorePlayerA - scorePlayerB >= 2) || (scorePlayerB >= 11 && scorePlayerB - scorePlayerA >= 2))) {
            displayForVersus("Please click \"Next Round\"");
        } else if (total_a == 4) {
            displayForVersus("Player A has won the game!");
        } else if (total_b == 4) {
            displayForVersus("Player B has won the game!");
        } else {
            scorePlayerA = scorePlayerA + 1;
            displayForPlayerA(scorePlayerA);
            if (scorePlayerA >= 11 && scorePlayerA - scorePlayerB >= 2) {
                displayForVersus("Player A has won this round");
            }
        }
    }


    int round1_a_score = 0;
    int round2_a_score = 0;
    int round3_a_score = 0;
    int round4_a_score = 0;
    int round5_a_score = 0;
    int round6_a_score = 0;
    int round7_a_score = 0;
    int round1_b_score = 0;
    int round2_b_score = 0;
    int round3_b_score = 0;
    int round4_b_score = 0;
    int round5_b_score = 0;
    int round6_b_score = 0;
    int round7_b_score = 0;

    int round1_a_foul = 0;
    int round2_a_foul = 0;
    int round3_a_foul = 0;
    int round4_a_foul = 0;
    int round5_a_foul = 0;
    int round6_a_foul = 0;
    int round7_a_foul = 0;
    int round1_b_foul = 0;
    int round2_b_foul = 0;
    int round3_b_foul = 0;
    int round4_b_foul = 0;
    int round5_b_foul = 0;
    int round6_b_foul = 0;
    int round7_b_foul = 0;

    public void nextRound(View v) {
        if ((total_a < 4 && total_b < 4) && ((scorePlayerA - scorePlayerB >= 2) || (scorePlayerB - scorePlayerA >= 2)) && (scorePlayerA >= 11 || scorePlayerB >= 11)) {
            if (scorePlayerA > scorePlayerB + 1) {
                total_a = total_a + 1;
            } else {
                total_b = total_b + 1;
            }
            if (total_a == 4) {
                displayForVersus("Player A has won the game!");
            } else if (total_b == 4) {
                displayForVersus("Player B has won the game!");
            } else if (total_a < 4 && total_b < 4) {
                displayForVersus(total_a + " - " + total_b);
                displayForPlayerA(0);
                displayForPlayerB(0);
            }

            if (round_n == 1) {
                round1_a_score = scorePlayerA;
                round1_b_score = scorePlayerB;
                round1_a_foul = foulPlayerA;
                round1_b_foul = foulPlayerB;
            } else if (round_n == 2) {
                round2_a_score = scorePlayerA;
                round2_b_score = scorePlayerB;
                round2_a_foul = foulPlayerA;
                round2_b_foul = foulPlayerB;
            } else if (round_n == 3) {
                round3_a_score = scorePlayerA;
                round3_b_score = scorePlayerB;
                round3_a_foul = foulPlayerA;
                round3_b_foul = foulPlayerB;
            } else if (round_n == 4) {
                round4_a_score = scorePlayerA;
                round4_b_score = scorePlayerB;
                round4_a_foul = foulPlayerA;
                round4_b_foul = foulPlayerB;
            } else if (round_n == 5) {
                round5_a_score = scorePlayerA;
                round5_b_score = scorePlayerB;
                round5_a_foul = foulPlayerA;
                round5_b_foul = foulPlayerB;
            } else if (round_n == 6) {
                round6_a_score = scorePlayerA;
                round6_b_score = scorePlayerB;
                round6_a_foul = foulPlayerA;
                round6_b_foul = foulPlayerB;
            } else if (round_n == 7) {
                round7_a_score = scorePlayerA;
                round7_b_score = scorePlayerB;
                round7_a_foul = foulPlayerA;
                round7_b_foul = foulPlayerB;
            }


            round_n = round_n + 1;

            scorePlayerA = 0;
            scorePlayerB = 0;
            foulPlayerA = 0;
            foulPlayerB = 0;

        } else if (total_a == 4) {
            displayForVersus("Player A has won the game!");
        } else if (total_b == 4) {
            displayForVersus("Player B has won the game!");
        } else {
            displayForVersus("This round is not over");
        }
    }


    public void resetScore(View v) {
        round_n = 1;
        scorePlayerA = 0;
        scorePlayerB = 0;
        foulPlayerA = 0;
        foulPlayerB = 0;
        total_a = 0;
        total_b = 0;
        round1_a_score = 0;
        round1_b_score = 0;
        round2_a_score = 0;
        round2_b_score = 0;
        round3_a_score = 0;
        round3_b_score = 0;
        round4_a_score = 0;
        round4_b_score = 0;
        round5_a_score = 0;
        round5_b_score = 0;
        round6_a_score = 0;
        round6_b_score = 0;
        round7_a_score = 0;
        round7_b_score = 0;

        round1_a_foul = 0;
        round1_b_foul = 0;
        round2_a_foul = 0;
        round2_b_foul = 0;
        round3_a_foul = 0;
        round3_b_foul = 0;
        round4_a_foul = 0;
        round4_b_foul = 0;
        round5_a_foul = 0;
        round5_b_foul = 0;
        round6_a_foul = 0;
        round6_b_foul = 0;
        round7_a_foul = 0;
        round7_b_foul = 0;

        displayForPlayerA(0);
        displayForPlayerB(0);
        displayForVersus("0 - 0");
    }


    public void showResult(View v) {
        Intent myIntent = new Intent(this, displayResultActivity.class);
        //pass multiple variables using bundle
        Bundle extras = new Bundle();
        extras.putInt("r1_a_score", round1_a_score);
        extras.putInt("r2_a_score", round2_a_score);
        extras.putInt("r3_a_score", round3_a_score);
        extras.putInt("r4_a_score", round4_a_score);
        extras.putInt("r5_a_score", round5_a_score);
        extras.putInt("r6_a_score", round6_a_score);
        extras.putInt("r7_a_score", round7_a_score);
        extras.putInt("r1_b_score", round1_b_score);
        extras.putInt("r2_b_score", round2_b_score);
        extras.putInt("r3_b_score", round3_b_score);
        extras.putInt("r4_b_score", round4_b_score);
        extras.putInt("r5_b_score", round5_b_score);
        extras.putInt("r6_b_score", round6_b_score);
        extras.putInt("r7_b_score", round7_b_score);

        extras.putInt("r1_a_foul", round1_a_foul);
        extras.putInt("r2_a_foul", round2_a_foul);
        extras.putInt("r3_a_foul", round3_a_foul);
        extras.putInt("r4_a_foul", round4_a_foul);
        extras.putInt("r5_a_foul", round5_a_foul);
        extras.putInt("r6_a_foul", round6_a_foul);
        extras.putInt("r7_a_foul", round7_a_foul);
        extras.putInt("r1_b_foul", round1_b_foul);
        extras.putInt("r2_b_foul", round2_b_foul);
        extras.putInt("r3_b_foul", round3_b_foul);
        extras.putInt("r4_b_foul", round4_b_foul);
        extras.putInt("r5_b_foul", round5_b_foul);
        extras.putInt("r6_b_foul", round6_b_foul);
        extras.putInt("r7_b_foul", round7_b_foul);

        extras.putInt("total_a", total_a);
        extras.putInt("total_b", total_b);
        myIntent.putExtras(extras);
        startActivity(myIntent);

    }

    /**
     * Displays the given score for A, B and versus.
     */
    public void displayForPlayerA(int score) {
        TextView scoreView = (TextView) findViewById(R.id.player_a_score);
        scoreView.setText(String.valueOf(score));
    }

    public void displayForPlayerB(int score) {
        TextView scoreView = (TextView) findViewById(R.id.player_b_score);
        scoreView.setText(String.valueOf(score));
    }

    public void displayForVersus(String string) {
        TextView text = (TextView) findViewById(R.id.vs_score);
        text.setText(String.valueOf(string));
    }

}

```

- activity_display_result.xml


```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context="com.example.android.scorekeeperpingpong.displayResultActivity">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@android:color/holo_green_light"
        android:orientation="horizontal"
        android:paddingBottom="16dp"
        android:paddingLeft="16dp"
        android:paddingRight="16dp"
        android:paddingTop="32dp">

        <TextView
            android:layout_width="72dp"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:text="" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:gravity="center"
            android:text="Player A"
            android:textColor="@android:color/black"
            android:textSize="18sp" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:gravity="center"
            android:text="Player B"
            android:textColor="@android:color/black"
            android:textSize="18sp" />


    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@android:color/holo_green_light"
        android:orientation="horizontal"
        android:paddingBottom="16dp"
        android:paddingLeft="16dp"
        android:paddingRight="16dp"
        android:paddingTop="16dp">


        <TextView
            android:layout_width="72dp"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:text="" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="0.5"
            android:gravity="center"
            android:text="Score"
            android:textSize="16sp" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="0.5"
            android:gravity="center"
            android:text="Foul"
            android:textSize="16sp" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="0.5"
            android:gravity="center"
            android:text="Score"
            android:textSize="16sp" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="0.5"
            android:gravity="center"
            android:text="Foul"
            android:textSize="16sp" />

    </LinearLayout>


    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:background="@android:color/holo_green_light"
        android:orientation="horizontal"
        android:paddingBottom="8dp"
        android:paddingLeft="16dp"
        android:paddingRight="16dp"
        android:paddingTop="8dp">


        <LinearLayout
            android:layout_width="72dp"
            android:layout_height="match_parent"
            android:orientation="vertical">

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="Round 1" />

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="Round 2" />

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="Round 3" />

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="Round 4" />

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="Round 5" />

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="Round 6" />

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="Round 7" />

        </LinearLayout>

        <LinearLayout
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:orientation="vertical"
            android:layout_weight="0.5">

            <TextView
                android:id="@+id/round1_a_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round2_a_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round3_a_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round4_a_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round5_a_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round6_a_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round7_a_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />
        </LinearLayout>


        <LinearLayout
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:orientation="vertical"
            android:layout_weight="0.5">

            <TextView
                android:id="@+id/round1_a_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round2_a_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round3_a_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round4_a_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round5_a_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round6_a_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round7_a_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:orientation="vertical"
            android:layout_weight="0.5">

            <TextView
                android:id="@+id/round1_b_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round2_b_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round3_b_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round4_b_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round5_b_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round6_b_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />

            <TextView
                android:id="@+id/round7_b_score"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />


        </LinearLayout>

        <LinearLayout
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:orientation="vertical"
            android:layout_weight="0.5">

            <TextView
                android:id="@+id/round1_b_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />
            <TextView
                android:id="@+id/round2_b_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />
            <TextView
                android:id="@+id/round3_b_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />
            <TextView
                android:id="@+id/round4_b_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />
            <TextView
                android:id="@+id/round5_b_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />
            <TextView
                android:id="@+id/round6_b_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />
            <TextView
                android:id="@+id/round7_b_foul"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0"
                android:textColor="@android:color/black" />
        </LinearLayout>


    </LinearLayout>


    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@android:color/holo_green_light"
        android:orientation="horizontal"
        android:padding="16dp">

        <TextView
            android:layout_width="72dp"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:text="TOTAL"
            android:textSize="18sp"
            android:textStyle="bold" />

        <TextView
            android:id="@+id/total_a"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:gravity="center"
            android:text=" "
            android:textColor="@android:color/black"
            android:textSize="18sp" />

        <TextView
            android:id="@+id/total_b"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:gravity="center"
            android:text=" "
            android:textColor="@android:color/black"
            android:textSize="18sp" />


    </LinearLayout>
</LinearLayout>
```

- displayResultActivity.java

```java

package com.example.android.scorekeeperpingpong;

import android.content.Intent;
import android.os.Bundle;
import android.support.v7.app.AppCompatActivity;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

import org.w3c.dom.Text;

public class displayResultActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_display_result);

        Bundle extras = getIntent().getExtras();
        int r1_a = extras.getInt("r1_a_score");
        TextView myText1_a = (TextView) findViewById(R.id.round1_a_score);
        myText1_a.setText(Integer.toString(r1_a));
        //If you provide an int as a parameter, it uses it as a resource ID, which, in this case, obviously doesn't exist.
        int r1_b = extras.getInt("r1_b_score");
        TextView myText1_b = (TextView) findViewById(R.id.round1_b_score);
        myText1_b.setText(Integer.toString(r1_b));

        int r2_a = extras.getInt("r2_a_score");
        TextView myText2_a = (TextView) findViewById(R.id.round2_a_score);
        myText2_a.setText(Integer.toString(r2_a));
        int r2_b = extras.getInt("r2_b_score");
        TextView myText2_b = (TextView) findViewById(R.id.round2_b_score);
        myText2_b.setText(Integer.toString(r2_b));

        int r3_a = extras.getInt("r3_a_score");
        TextView myText3_a = (TextView) findViewById(R.id.round3_a_score);
        myText3_a.setText(Integer.toString(r3_a));
        int r3_b = extras.getInt("r3_b_score");
        TextView myText3_b = (TextView) findViewById(R.id.round3_b_score);
        myText3_b.setText(Integer.toString(r3_b));

        int r4_a = extras.getInt("r4_a_score");
        TextView myText4_a = (TextView) findViewById(R.id.round4_a_score);
        myText4_a.setText(Integer.toString(r4_a));
        int r4_b = extras.getInt("r4_b_score");
        TextView myText4_b = (TextView) findViewById(R.id.round4_b_score);
        myText4_b.setText(Integer.toString(r4_b));

        int r5_a = extras.getInt("r5_a_score");
        TextView myText5_a = (TextView) findViewById(R.id.round5_a_score);
        myText5_a.setText(Integer.toString(r5_a));
        int r5_b = extras.getInt("r5_b_score");
        TextView myText5_b = (TextView) findViewById(R.id.round5_b_score);
        myText5_b.setText(Integer.toString(r5_b));

        int r6_a = extras.getInt("r6_a_score");
        TextView myText6_a = (TextView) findViewById(R.id.round6_a_score);
        myText6_a.setText(Integer.toString(r6_a));
        int r6_b = extras.getInt("r6_b_score");
        TextView myText6_b = (TextView) findViewById(R.id.round6_b_score);
        myText6_b.setText(Integer.toString(r6_b));

        int r7_a = extras.getInt("r7_a_score");
        TextView myText7_a = (TextView) findViewById(R.id.round7_a_score);
        myText7_a.setText(Integer.toString(r7_a));
        int r7_b = extras.getInt("r7_b_score");
        TextView myText7_b = (TextView) findViewById(R.id.round7_b_score);
        myText7_b.setText(Integer.toString(r7_b));





        int f1_a = extras.getInt("r1_a_foul");
        TextView myTextf1_a = (TextView) findViewById(R.id.round1_a_foul);
        myTextf1_a.setText(Integer.toString(f1_a));
        //If you provide an int as a parameter, it uses it as a resource ID, which, in this case, obviously doesn't exist.
        int f1_b = extras.getInt("r1_b_foul");
        TextView myTextf1_b = (TextView) findViewById(R.id.round1_b_foul);
        myTextf1_b.setText(Integer.toString(f1_b));

        int f2_a = extras.getInt("r2_a_foul");
        TextView myTextf2_a = (TextView) findViewById(R.id.round2_a_foul);
        myTextf2_a.setText(Integer.toString(f2_a));
        int f2_b = extras.getInt("r2_b_foul");
        TextView myTextf2_b = (TextView) findViewById(R.id.round2_b_foul);
        myTextf2_b.setText(Integer.toString(f2_b));

        int f3_a = extras.getInt("r3_a_foul");
        TextView myTextf3_a = (TextView) findViewById(R.id.round3_a_foul);
        myTextf3_a.setText(Integer.toString(f3_a));
        int f3_b = extras.getInt("r3_b_foul");
        TextView myTextf3_b = (TextView) findViewById(R.id.round3_b_foul);
        myTextf3_b.setText(Integer.toString(f3_b));

        int f4_a = extras.getInt("r4_a_foul");
        TextView myTextf4_a = (TextView) findViewById(R.id.round4_a_foul);
        myTextf4_a.setText(Integer.toString(f4_a));
        int f4_b = extras.getInt("r4_b_foul");
        TextView myTextf4_b = (TextView) findViewById(R.id.round4_b_foul);
        myTextf4_b.setText(Integer.toString(f4_b));

        int f5_a = extras.getInt("r5_a_foul");
        TextView myTextf5_a = (TextView) findViewById(R.id.round5_a_foul);
        myTextf5_a.setText(Integer.toString(f5_a));
        int f5_b = extras.getInt("r5_b_foul");
        TextView myTextf5_b = (TextView) findViewById(R.id.round5_b_foul);
        myTextf5_b.setText(Integer.toString(f5_b));

        int f6_a = extras.getInt("r6_a_foul");
        TextView myTextf6_a = (TextView) findViewById(R.id.round6_a_foul);
        myTextf6_a.setText(Integer.toString(f6_a));
        int f6_b = extras.getInt("r6_b_foul");
        TextView myTextf6_b = (TextView) findViewById(R.id.round6_b_foul);
        myTextf6_b.setText(Integer.toString(f6_b));

        int f7_a = extras.getInt("r7_a_foul");
        TextView myTextf7_a = (TextView) findViewById(R.id.round7_a_foul);
        myTextf7_a.setText(Integer.toString(f7_a));
        int f7_b = extras.getInt("r7_b_foul");
        TextView myTextf7_b = (TextView) findViewById(R.id.round7_b_foul);
        myText7_b.setText(Integer.toString(f7_b));


        int tot_a = extras.getInt("total_a");
        TextView myTextT_a = (TextView) findViewById(R.id.total_a);
        myTextT_a.setText(Integer.toString(tot_a));

        int tot_b = extras.getInt("total_b");
        TextView myTextT_b = (TextView) findViewById(R.id.total_b);
        myTextT_b.setText(Integer.toString(tot_b));

    }
}
```
