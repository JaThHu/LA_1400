package JanickHurschler;
import robocode.*;

public class EZZWIN extends JuniorRobot
{
	
	int heightdistance;
	int widthdistance;

	public void run() {
		
		setColors(white, white, white, yellow, black);
		
		while(true) {
			
			avoidWall();
			
			moveInCircles();
			
			bearGunTo(0);
				
		}
	}
		
	public void onScannedRobot() {
		
		schootSmart();
			
	}

	public void onHitByBullet() {
		
		escapeFromEnemies();
		
	}
	
	public void onHitWall() {
		
		back(20);
		turnRight(180);
		
	}	

	public void onHitRobot() { 
		
		huntAndKillEnemies();
		
	}
	

	public void moveInCircles(){

		ahead(50);
		turnRight(20);
		ahead(50);
		turnRight(20);
		ahead(50);
		turnRight(20);
		ahead(50);
		turnRight(20);
		ahead(50);
		
	}
	
	public void avoidWall() {
	
		heightdistance = fieldHeight - robotY;
		widthdistance = fieldWidth - robotX;
			
		if(heightdistance <= 100 || widthdistance <= 100){
				
			turnLeft(180);
				
		}
	}
	
	public void schootSmart(){

		if (others <= 8){
		bearGunTo(scannedBearing);
		fire(1);
		}
	}
	
	public void escapeFromEnemies(){

		turnAheadLeft(50, 70);
		
	}
	
	public void huntAndKillEnemies(){

		bearGunTo(scannedBearing);
		turnTo(scannedBearing);
		ahead(50);
		fire(1);
		
	}
	
}

