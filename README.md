<!DOCTYPE html>

<html>

  <head>
    <meta charset="UTF-8">
    <title>Canvas</title>

    <style type="text/css">
      canvas {
        border: 1px solid black;
      }
    </style>

  </head>

  <body>
        
      <canvas id="tim's-game" width="800px" height="600px"></canvas>
      
      <script type="text/javascript">
          // up top. creates the canvas with given dimensions
          // declares script type
          
      
          // Gets a handle to the element with id canvasOne.      
          var canvas = document.getElementById("tim's-game");      
          // Get a 2D context for the canvas.     
          var ctx = canvas.getContext("2d");	  
       
          // Creates object for the balls 
          var ball = {
              // determines the position where the ball will apear math.random gives a random position on the x ace
              position: {x: Math.floor((Math.random() * 780) + 20), y: 10}
              // Will determine the size of the ball
              , radius: 6
              // Will determine the speed of the ball
              , velocity: {x: 3, y: 0}
              // Will determine if the ball will get faster or slower
              , acceleration: {x: 0, y: 0.1}        
              // Function that draws the ball  
              ,drawBall: function(){                  
                  // Collour of the object         
                  ctx.fillStyle = "rgb(25, 100, 100)";  
                  // begins path
                  ctx.beginPath();
                  // calls the object it will draw with positions and size
                  ctx.arc(ball.position.x, ball.position.y, ball.radius, 0, 2 * Math.PI);
                  // fills the colour 
                  ctx.fill();       
                  
	
                  // Update the y location.
                  ball.velocity.y += ball.acceleration.y;
                  ball.position.x += ball.velocity.x;
                  ball.position.y += ball.velocity.y;
                  // Keep the animation going while the ball has not touched the canvas bottom.
                  // Note there's a bug here.
                  if ((ball.position.x >= canvas.width - ball.radius) ||  (ball.position.x <=                 ball.radius))
                      ball.velocity.x = -ball.velocity.x;    
                  if ((ball.position.y >= canvas.height - ball.radius) ||  (ball.position.y <=              ball.radius))
                      ball.velocity.y = -ball.velocity.y;
                  
                  
              }
          }
          
          // Created a second ball object
          var ball2 = {
              // determines the position where the ball will apear math.random gives a random position on the x ace
              position: {x: Math.floor((Math.random() * 780) + 20), y: 10}
              // Will determine the size of the ball
              , radius: 6
              // Will determine the speed of the ball
              , velocity: {x: 3, y: 0}
              // Will determine if the ball will get faster or slower
              , acceleration: {x: 0, y: 0.1}        
              // Function that draws the ball  
              ,drawBall2: function(){                  
                  // Collour of the object         
                  ctx.fillStyle = "rgb(25, 100, 100)";  
                  // begins path
                  ctx.beginPath();
                  // calls the object it will draw with positions and size
                  ctx.arc(ball2.position.x, ball2.position.y, ball2.radius, 0, 2 * Math.PI);
                  // fills the colour 
                  ctx.fill();       
                  
	
                  // Update the y location.
                  ball2.velocity.y += ball2.acceleration.y;
                  ball2.position.x += ball2.velocity.x;
                  ball2.position.y += ball2.velocity.y;
                  // Keep the animation going while the ball has not touched the canvas bottom.
                  // Note there's a bug here.
                  if ((ball2.position.x >= canvas.width - ball2.radius) ||  (ball2.position.x <= ball2.radius))
                      ball2.velocity.x = -ball2.velocity.x;    
                  if ((ball2.position.y >= canvas.height - ball2.radius) ||  (ball2.position.y <= ball2.radius))
                      ball2.velocity.y = -ball2.velocity.y;
              }
          }
        
          
         
          

          
          // Creates a new ball object 
          // This ball will be used for moving around the canvas
          var ballm = {
              // spawns the ball in the middle of the canvas
              x: canvas.width / 2
              , y: canvas.height / 2
              , r: 50
          };
            
          // Creates a draw circle function
          function drawCircle() {
              ctx.fillStyle = "rgb(255, 0, 0)";
              ctx.beginPath();
              ctx.arc(ballm.x, ballm.y, ballm.r, 0, 2 * Math.PI);
              ctx.fill();
          }
                    
          function collideWithBall() {
			
              if (ballm.x + ball.r == ball.x + ball.radius && ballm.position.y + ball.radius == ball.position.y +ball.radius ){
                
                  //gameOver();
                
                  ctx.clearRect(0, 0, canvas.width, canvas.height);
                
                  ctx.fillStyle = "black";
                
                  ctx.font = "18px Arial";
                
                  ctx.fillText("Game Over ", 300, 200);
            }              
              else{                
                  return;
              
              }				
			
		
          }
          // A function to repeat every time the animation loops.
          function repeatme() {
              if (ballm.x + ballm.r <= ball.x + ball.r ){
                
                  //gameOver();
                
                  ctx.clear;
                  //Rect(0, 0, canvas.width, canvas.height);
                
                  ctx.fillStyle = "black";
                
                  ctx.font = "18px Arial";
                
                  ctx.fillText("Game Over ", 300, 200);
            }
              
              // clears  the screan/canvas i.e. where the ball was previously does not show up.
              ctx.clearRect(0, 0, canvas.width, canvas.height);
              // calls the function in the ball object
              ball.drawBall();
              
              
              
              ball2.drawBall2();
              //calls the draw circle function
              drawCircle();
              
               
              
              
              //collideWithBall();
              // gets the animation going
              window.requestAnimationFrame(repeatme);  
          }
          
          // Add an event listener to the keypress event.          
          window.addEventListener("keydown", function(event) {
              
              ctx.clearRect(0, 0, canvas.width, canvas.height);
              
              // Right
              if (event.keyCode == 39 && ballm.x < canvas.width - ballm.r)
                  ballm.x += Math.min(10, canvas.width - ballm.x - ballm.r);

              // Left
              else if (event.keyCode == 37 && ballm.x > ballm.r)
                  ballm.x -= 10;
        
              // down
              else if (event.keyCode == 40 && ballm.y < canvas.height - ballm.r)
                  ballm.y += 10;
        
              // For up movement
              else if (event.keyCode == 38 && ballm.y > ballm.r)
                  // updates location by int given
                  ballm.y -= 10;
        
              drawCircle();
      
          });
   
      
          // Get the animation going.
      
          window.requestAnimationFrame(repeatme);
    </script>

  </body>

</html>
