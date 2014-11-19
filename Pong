import processing.core.*; 
import processing.data.*; 
import processing.event.*; 
import processing.opengl.*; 

import java.io.BufferedWriter; 
import java.io.File; 
import java.io.FileWriter; 
import java.io.IOException; 
import ddf.minim.*; 

import java.util.HashMap; 
import java.util.ArrayList; 
import java.io.File; 
import java.io.BufferedReader; 
import java.io.PrintWriter; 
import java.io.InputStream; 
import java.io.OutputStream; 
import java.io.IOException; 

public class Pong extends PApplet {

// Naveed Shihab Java Intensive Project







float xSpeed = 2;
PImage mario1;
PImage mario2;
PImage mario3;
PImage cloud1;
PImage wing1;
PImage wing2;
PImage baloon1;
PImage cloud2;
PImage cloud3;
PImage pipe1;
PImage tree1;
PImage gate1;
PImage gameOverScreen1;
PImage star1;
PImage bigBullet2;
PImage enemy;

int highScore[];
int highestScore;

Minim minim;
AudioPlayer blockHIT;
AudioPlayer paddleHIT;
AudioPlayer music;
AudioPlayer gameOverSong;

int grr = 0;
int newStuff;
float ySpeed = 3;

float marioX = 400;
float marioY = 355;
float enemyX = random(0, 500);
float enemyY = -15;

boolean gameOver;
// position of ball centre
float ballX = 20; 
float ballY = 20;

float ballRadius = 8;
float blockSize = 40;
float paddleWidth = 80;
float paddleHeight = 15;
int score = 0;
float blockReducer = 0;
boolean blockHit;
String scorePrint = "";
float blockCounter = 1;
float baloonCheck;
float baloonX = 550;
float baloonY = 90;
float baloonBx = -230;
float baloonBy = 180;
float cloud2X = 50;
float cloud2Y = 150;
boolean lifeCheck = false;
int life = 0;
String lifePrint = "";
String highScorePrint = "";
boolean starPick = false;
boolean gameMode = true;

boolean paddleBash = false;
boolean cloudCheck = false;
boolean isGameOver = false;
float wingCounter = 0;

PFont f;
String[] stuff = loadStrings("C:\\Users\\Naveed PC\\Desktop\\CITY\\Modules\\Java Intensive\\HOME RUN\\Day 2\\Pong\\highscore.txt");

public void setup() 
{
  size(495, 500, P3D);
  minim = new Minim(this);
  highScore = PApplet.parseInt(split(stuff[0], ','));

  blockHIT = minim.loadFile("$RVQZLTU.wav");
  paddleHIT = minim.loadFile("$RYEXPRY.wav");
  music = minim.loadFile("Music Background.mp3");
  gameOverSong = minim.loadFile("Game Over.mp3");
  mario1 = loadImage("mario1.png");
  mario2 = loadImage("mario2.png");
  mario3 = loadImage("mario3.png");
  cloud1 = loadImage("cloud1.png");
  cloud2 = loadImage("cloud2.png");
  cloud3 = loadImage("cloud3.png");
  wing1 = loadImage("wing1.png");
  wing2 = loadImage("wing2.png");
  baloon1 = loadImage("baloon1.png");
  pipe1 = loadImage("pipe1.png");
  tree1 = loadImage("tree1.png");
  gate1 = loadImage("gate1.png");
  gameOverScreen1 = loadImage("gameOverScreen1.jpg");
  star1 = loadImage("star1.png");
  bigBullet2 = loadImage("bigBullet1.png");
  enemy = loadImage("enemy.png");
  music.play();
  music.loop();
}

public void draw() 
{
  ballX = ballX + xSpeed + random(-0.02f, 0.02f);
  newStuff = Integer.parseInt(stuff[0]);
  if (gameOver == true)
  {
    gameOverScreen1(0, 0);
    //noLoop();
    text("Your", 363, height - 166, width, height);
    text("Score :", 355, height - 130, width, height);
    text("High", 63, height - 166, width, height);
    text("Score :", 55, height - 130, width, height);
    
    if (score < newStuff && score < 100 && score > 9)
    {
      text(stuff[0], 76, height - 89, width, height);  
    }
    
    if (score < newStuff && score < 10)
    {
      text(stuff[0], 86, height - 89, width, height);  
    }
    
    if (score < newStuff && score > 99)
    {
      text(stuff[0], 66, height - 89, width, height);  
    }
    
    if (score > newStuff)
    {
      text(highScorePrint, 66, height - 89, width, height);   
    }
    
    if (score < 10)
    {
      text(scorePrint, 385, height - 89, width, height);
    }

    if (score > 9 && score < 100)
    {
      text(scorePrint, 376, height - 89, width, height);
    }
    
    if (score > 99)
    {
      text(scorePrint, 367, height - 89, width, height); 
    }
    
    highScorePrint = Integer.toString(score);
  }

  if (gameMode == true && gameOver == false)
  {
    lifeCheck = false;
    gameOver = false;
    background(0xffE8985B);
    drawPaddle();
    scorePrint = Integer.toString(score);
    lifePrint = Integer.toString(life);
    textSize(30);
    //drawStar1Sized();
    
    if(score <= newStuff)
    {
      fill(0xff000000);
      textSize(15);
      text("High Score: " + stuff[0], 265, -13, width/2, height/2);  
    }
    
    if(score > newStuff)
    {
      fill(0xff000000);
      textSize(15);
      text("High Score: " + score, 285, -13, width/2, height/2);  
    }
    
    textSize(30);
    
    drawPipe1(283, 350);

    for (int i = 50; i < 401; i = i + 50)
    {
      if (i < 251 || i > 301)
      {
        if ((i < 151 || i > 201) && (i < 51 || i > 101))
        {
          drawTree1(i, marioY - 5);
          if ((i < 101 || i > 151) && (i < 301 || i > 351))
          {
            drawSmallTree(i - 20, 350 - 5);
          }
          else
          {
            drawSmallTree(i - 20, 350 - 15);
          }
        }
      }
    }

    drawCloudSizer(cloud2X + 120, cloud2Y - 80, 100, 80);
    drawCloudSizer(cloud2X - 100, cloud2Y + 50, 70, 30);
    drawCloudSizer(cloud2X - 125, cloud2Y, 30, 40);
    drawCloud3(cloud2X - 50, cloud2Y - 50);

    baloonX = baloonX - 0.2f;
    baloonBx = baloonBx + 0.1f;
    drawBaloon1(baloonX, baloonY);
    drawSmallBaloon1(baloonBx, baloonBy);

    cloudCheck = false;
    cloud2X = cloud2X + 0.1f;
    drawCloudSizer(cloud2X + 230, cloud2Y - 40, 30, 30);
    drawCloudSizer2(cloud2X - 250, cloud2Y - 120, 110, 90);
    drawCloud2(cloud2X, cloud2Y);

    if (marioX < -40)
    {
      marioX = 490;
    }   
    
    if (baloonX == 0)
    {
      baloonX = 500;
    }

    if (baloonBy == 700)
    {
      baloonX = 500;
    }

    if (blockCounter % 2 == 0 && paddleBash != true)
    {
      if (marioX < -40)
      {
        marioX = 490;
      }  
      drawMario1(marioX, marioY);
    }
    if (blockCounter %2 != 0 && paddleBash != true)
    {
      if (marioX < -40)
      {
        marioX = 490;
      }  
      drawMario2(marioX, marioY);
    }

    if (paddleBash && score > 0)
    {
      if (marioX < -40)
      {
        marioX = 490;
      } 
      marioX = marioX - 0.3f;
      drawMario3(marioX, marioY - 5);
    }
    if (marioX > 112 && marioX < 425)
    {
      drawStar1(81, 375);
    }

    drawPipe1(180, 370);
    drawBigTree(130, 370);
    drawBigTree(330, 360);

    if (marioX > 140 && marioX < 145)
    {
      starPick = true;
    }

    if (score > 0)
    {
      if (marioX < 113 && marioX > 112)
      {
        if (starPick == true)
        {
          life = life + 1;
          starPick = false;
        }
        lifeCheck = true;    
      }
      drawStar1Sized(420, 280, star1.width*2, star1.height*2);
      lifePrint = Integer.toString(life);
      text(" x" + lifePrint, width - 65, height - 207, width, height);
      grr = 255;
    }

    // add the ball speed to the x and y locations
    ballX = ballX + xSpeed;
    ballY = ballY + ySpeed;

    // check for collisions with walls
    if ((ballX + ballRadius > width && xSpeed > 0) || (ballX - ballRadius < 0 && xSpeed < 0)) 
    {

      xSpeed = xSpeed * -1;
    }

    if (ballY + ballRadius > height)
    {
      life = life - 1;
      if(life == -1)
      {
        //minim.stop();
        gameOver = true;
        drawPaddle();
        fill(0xff0A0000);
        textSize(15);
        text("GAME OVER!", 5, height - 40, width, height);
        fill(0xffB23232);
        textSize(40);
        isGameOver = true;
        gameMode = false;
        gameOverSong.play();
        gameOverScreen1(0, 0);
        saveHighScore();
      }
    }

    if ((ballY + ballRadius > height && ySpeed > 0) || (ballY - ballRadius < 0 && ySpeed < 0))
    {
      ySpeed = ySpeed * -1;
    }

    // display the ball at its current location

    if (!gameOver)
    {
      stroke(0);
      fill(0xffC66922);
    }
    else
    {
      noStroke();
      noFill();
    } 
    ellipse(ballX, ballY, ballRadius * 2, ballRadius * 2);

    for (int row = 25; row <= 275; row = row + 100) 
    {
      for (int col = 25; col <= 475; col = col + 100)
      {
        if (!isGameOver)
        {
          if (col == 225 && row == 125)
          {
            //
          }
          else
          {
            drawBlock(col, row);
            blockCollisionCheck(col, row);

            //drawCloud2(col, row);
            fill(0xff890707, grr);
            textSize(24);

            if (score > 0 && score < 10)
            {
              stroke(0xffFFFCFC);
              text(scorePrint, 14 + col, row + 1, width, height);
            }

            if (score < 100 && score > 9)
            {
              stroke(0xffFFFCFC);
              text(scorePrint, 3 + col, row + 1, width, height);
            }
            
            if(score > newStuff)
            {
              if(score > 99)
              {
                stroke(0xffFFFCFC);  
                textSize(45);
                text(scorePrint, 210, 132, width, height);
              }
              
              if(score < 10)
              {
                stroke(0xffFFFCFC);  
                textSize(45);
                text(scorePrint, 230, 132, width, height);
              }
              
              if(score < 100 && score > 9)
              {
                stroke(0xffFFFCFC);  
                textSize(45);
                text(scorePrint, 220, 132, width, height);  
              }
            }
          }
        }
      }
    }
  }
}

/**
 * Test if ball has collided with a stationary block whose top-left corner is at
 * (x,y) and reverse the ball's motion according to which sides it hit.
 */
public void blockCollisionCheck(float x, float y) 
{
  // treat the ball as a square for the purposes of collision detection
  if (ballY + ballRadius >= y && ballY - ballRadius <= y + blockSize && ballX + ballRadius >= x && ballX - ballRadius <= x + blockSize) 
  {
    // the ball is overlapping the block

    // position of ball centre in previous frame
    float pballX = ballX - xSpeed; 
    float pballY = ballY - ySpeed;

    // approximate test for whether a horizontal face has been hit: check if previous ball position was above/below block
    if ((pballY + ballRadius < y) || (pballY - ballRadius > y + blockSize)) 
    {
      paddleBash = false;
      blockCounter = blockCounter + 1;
      marioX = marioX - 1;

      blockHIT.play();
      blockHit = true;
      blockReducer = blockReducer + 10;
      ySpeed = -ySpeed;
    }

    // approximate test for whether a vertical face has been hit: check if previous ball position was left/right of block
    if ((pballX + ballRadius < x) || (pballX - ballRadius > x + blockSize)) 
    {
      paddleBash = false;
      blockCounter = blockCounter + 1;
      marioX = marioX - 1;

      blockHIT.play();
      blockHit = true;
      blockReducer = blockReducer + 10;
      xSpeed = -xSpeed;
    }
  }
}

public void drawBlock(float x, float y) 
{
  if (!isGameOver)
  { 
    noFill();
    strokeWeight(4);
    stroke(0xff000000);

    cloudCheck = true;

    if (blockHit)
    {
      if (blockCounter % 2 == 0 && score < 6)
      {
        drawCloud1(x + 30, y - 40);
      }
      if (blockCounter % 2 != 0 && score < 6)
      {
        drawCloud1(x - 30, y - 40);
      }

      if (score > 4)
      {
        if (blockCounter %5 == 0)
        {
          drawWing1(x - 30, y - 40);
        }

        if (blockCounter %5 != 0)
        {
          drawWing1(x + 30, y + 40);
        }
      }

      if (score > 14 && blockCounter %4 == 0)
      {
        drawWing2(x - 70, y + 25);
      }

      if (score > 9)
      {
        drawBigBullet2(x - 50, y + 60);
      }

      if (score > 10 && blockCounter %3 == 0)
      {
        drawBigBullet2(x + 50, y - 60);
      }

      stroke(0);
      strokeWeight(1);
      ellipse(x, y, blockSize - blockReducer, blockSize - blockReducer);
    }

    else
    {
      strokeWeight(1);
      stroke(0xff000000);
      fill(0xffE89696, 0);
      rect(x, y, blockSize, blockSize);

      drawCloud1(x, y);
      drawCloud2(x, y);
    }
    blockHit = false;
  }
}

public void drawPaddle()
{
  if (!gameOver)
  {
    fill(0xffC66922, grr);
    stroke(0xff000000);
    tint(235);
  }
  if (gameOver)
  {
    fill(0xffE8985B, 50);
    stroke(0xffE8985B);
    tint(235);
  }
  rect(mouseX - 40, 470, 80, 20);
  if (score > 0)
  {
    drawStar1Sized(mouseX - 9, 473, star1.width/2, star1.height/2);
  }
  paddleCollisionCheck(mouseX - 40, 470);
}

public void paddleCollisionCheck(float mouseX, float y)
{
  // treat the ball as a square for the purposes of collision detection
  if (ballY + ballRadius >= y && ballY - ballRadius <= y + paddleHeight && ballX + ballRadius >= mouseX && ballX - ballRadius <= mouseX + paddleWidth) 
  {
    // the ball is overlapping the block

    // position of ball centre in previous frame
    float pballX = ballX - xSpeed; 
    float pballY = ballY - ySpeed;

    // approximate test for whether a horizontal face has been hit: check if previous ball position was above/below block
    if ((pballY + ballRadius < y) || (pballY - ballRadius > y + paddleHeight)) 
    {
      if (ySpeed < 8)
      {
        paddleHIT.play();
        ySpeed = -ySpeed-0.2f;
        paddleBash = true;
        //jumpSmall.play();
      }
      else
      {
        paddleHIT.play();
        ySpeed = -ySpeed;
        paddleBash = true;
        //jumpSmall.play();
      }
      score = score + 1;
      scorePrint = Integer.toString(score);
    }

    // approximate test for whether a vertical face has been hit: check if previous ball position was left/right of block
    if ((pballX + ballRadius < mouseX) || (pballX - ballRadius > mouseX + paddleWidth)) 
    {
      xSpeed = -xSpeed;
    }
  }
}

public void drawMario1(float x, float y)
{
  image(mario1, x, y - 8, 50, 100);
}

public void drawMario2(float x, float y)
{
  image(mario2, x, y - 8, 50, 100);
}

public void drawMario3(float x, float y)
{
  image(mario3, x, y + 8, 50, 60);
}

public void drawCloud1(float x, float y)
{
  image(cloud1, x, y, blockSize, blockSize);
}

public void drawCloud2(float x, float y)
{
  if (!cloudCheck)
  {
    image(cloud2, x, y, 100, 50);
  }
  else
  {
    image(cloud2, x, y, blockSize, blockSize);
  }
}

public void drawCloud3(float x, float y)
{
  image(cloud3, x, y, 120, 60);
}

public void drawCloudSizer(float x, float y, float a, float b)
{
  image(cloud3, x, y, a, b);
}

public void drawCloudSizer2(float x, float y, float a, float b)
{
  image(cloud2, x, y, a, b);
}

public void drawWing1(float x, float y)
{
  image(wing1, x, y, wing1.width, wing1.height);
}

public void drawWing2(float x, float y)
{
  image(wing2, x, y, wing2.width, wing2.height);
}

public void drawBaloon1(float x, float y)
{
  image(baloon1, x, y, baloon1.width/2, baloon1.height/2);
}

public void drawSmallBaloon1(float x, float y)
{
  image(baloon1, x, y, baloon1.width/4, baloon1.height/4);
}

public void drawPipe1(float x, float y)
{
  image(pipe1, x, y, pipe1.width, pipe1.height);
}

public void drawTree1(float x, float y)
{
  image(tree1, x, y, tree1.width/1.5f, tree1.height/1.5f);
}

public void drawSmallTree(float x, float y)
{
  image(tree1, x, y, tree1.width/2, tree1.height/2);
}

public void drawBigTree(float x, float y)
{
  image(tree1, x, y, tree1.width/1.2f, tree1.height/1.2f);
}

public void drawGate1(float x, float y)
{
  image(gate1, x, y, gate1.width, gate1.height);
}

public void gameOverScreen1(float x, float y)
{
  image(gameOverScreen1, x, y, gameOverScreen1.width, gameOverScreen1.height);
}

public void drawStar1(float x, float y)
{
  image(star1, x, y, star1.width, star1.height);
}

public void drawStar1Sized(float x, float y, float a, float b)
{
  image(star1, x, y, a, b);
}

public void drawBigBullet2(float x, float y)
{
  image(bigBullet2, x, y, bigBullet2.width, bigBullet2.height);
}

public void mouseClicked()
{
  if (gameOver == true)
  {
    println(mouseX + " " + mouseY);
  }
}

public void saveHighScore()
{
  String[] data = new String[highScore.length];

  if (score > highScore[0])
  {
    data[0] = Integer.toString(score);
    highestScore = score;
    saveStrings("highscore.txt", data);
  }
}
  static public void main(String[] passedArgs) {
    String[] appletArgs = new String[] { "Pong" };
    if (passedArgs != null) {
      PApplet.main(concat(appletArgs, passedArgs));
    } else {
      PApplet.main(appletArgs);
    }
  }
}
