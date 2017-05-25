/* Name: Srilatha Mada
 * Assignment No.3
 * Date: 3/08/2017
 * Class: SP17 - CS585A - JAVA PROGRAMMING
 */


import java.util.Arrays;
import java.util.Scanner;
public class ConnectN 
{
	private int gameState[][]; 
	private int rows; 
	private int columns; 
	private int winningNumber; 
	private int lastRow, lastColumn;
	private static Scanner scanner = new Scanner(System.in);
	private int player;
	public ConnectN() 
	{
		//initialize
		//initialize class variables to default parameters
		//rows = 6 //columns = 7 //winning number = 4 
		//initialize game state //initialize lastRow and lastColumnthis.rows = 6;
		this.columns = 7;
		this.winningNumber = 4;
		gameState = new int[rows][columns];
		this.lastRow = -1;
		this.lastColumn = -1;
		this.player = 1;
		
	}
	public ConnectN(int rows, int columns, int winningNumber) 
	{
		//initialize
		//initialize class variables based on input parameters //initialize game state 
		//initialize lastRow and lastColumn
		this.rows = rows;
		this.columns = columns;
		this.winningNumber = winningNumber;
		gameState = new int[rows][columns];
		this.lastRow = -1;
		this.lastColumn = -1;
		this.player = 1;
	}


	public void resetGame()
	{
		
		//set lastRow and lastColumn to -1 //set all positions to empty
		this.lastRow = -1;
		this.lastColumn = -1;
		this.player = 1;
		for (int i = 0; i<gameState.length; i++)
		{
			Arrays.fill(gameState[i], 0);
		}
	}
	public boolean insertChip(int playerNumber, int columnNumber)
	{
		boolean inserted = false; //try to insert
		//if the top position is empty
		//start at row 0 (the top row) 
		//loop through the rows until a non-empty position is found
		//set game state position to the player number 
		//inserted = true //set last row and last column to the inserted position
		for (int i = 0; i<gameState.length && !inserted; i++)
		{
			if (gameState[i][columnNumber-1] == 0)
			{
				gameState[i][columnNumber-1] = playerNumber;
				inserted = true;
				lastRow = i;
				lastColumn = columnNumber-1;
			}
		}
		
		return inserted;
	}
	public void outputGameState() 
	{ 
		//create a string builder
		StringBuilder strBuilder = new StringBuilder();
		
		//loop through all rows
		for (int i = gameState.length-1; i>=0; i--)
		{
			//loop through all columns
			for (int j = 0; j<gameState[i].length; j++)
			{
				//append gameState[row][column] to the output string builder
				strBuilder.append(gameState[i][j]);
				strBuilder.append("\t");
			}
			strBuilder.append("\n");
		}
		//output the game state string
		System.out.println(strBuilder.toString());
	}

	private boolean isGameFull()
	{ 
		boolean isFull = true;
		//check if game board is full //loop through all columns
		for (int col = 0; col<this.columns; col++)
		{
			//if the top position is empty then the game is not full
			if(gameState[this.rows-1][col]==0)
				isFull = false;
		}
		return isFull;
	}
	
	public int detectWin()
	{ 
		int winner = -1;
		//detect win rows //detect win columns //detect win diagonals
		//return winner; 
		winner = detectWinRows();
		if (winner != 1)
		{
			winner = detectWinColumns();
			if (winner != 1)
			{
				winner = detectWinDiagonals();
			}
		}
		return winner;
	}
	private int detectWinColumns()
	{
		int winColumns = 0;
		int count = 1;
		boolean search = true;
		//return the player who won or 0 if no player has won int winColumns = 0; 
		//start at last posotion
		//loop down the column as far as needed 
		//set winColumn if count of number in a row is greater than winning number
		for (int i = this.lastRow-1; i>=0 && count<this.winningNumber && search; i--)
			{
				if (gameState[i][this.lastColumn] == player)
				{
					count++;
				}
				else
					search = false;
			}
		
		
		if (count>=winningNumber)
			winColumns=1;
	
	return winColumns;
	}
	
	private int detectWinRows()
	{ 
		int winRows = -1;
		player = gameState[lastRow][lastColumn];
		int count = 1;
		boolean stopLeft = false;
		boolean stopRight = false;
		//left size //loop starting at lastColumn-1 until out of bounds or stopLeft = false
		//if current position == player //increment count //else //stopLeft = true
		for (int i=lastColumn-1; i>=0 && !stopLeft && count<winningNumber; i--)
		{
			
			if (gameState[lastRow][i] == player)
			{
				count++;
			}
			else
				stopLeft = true;
			//count of chips in a row boolean stopLeft = false; //stop searching to the left boolean stopRight = false; //stop searching to the right
		}
		
		if (stopLeft || count <winningNumber)
			//right side (similiar to left side)
			for (int i=lastColumn+1; i<columns && count < winningNumber && !stopRight; i++)
			{
				if (gameState[lastRow][i] == player)
					count++;
				else
					stopRight = true;
				
			}
		if (count>=winningNumber)
			winRows = 1;
	
	
		//if count >= winningNumber set winRows to the last player
		return winRows;
	}
	private int detectWinDiagonals()
	{
		int winDiagonals = -1;
		player = gameState[lastRow][lastColumn];
		int countLeftToRight = 1; //count in a row for diagonals from left to right
		int countRightToLeft = 1;  //count in a row for diagonals from right to left
		boolean stopLeft1 = false; //stop searching to the left (diagonal left to right)
		boolean stopRight1 = false; //stop searhcing to the right (diagonal right to left)
		boolean stopLeft2 = false; //stop searching to the left (diagonal left to right)
		boolean stopRight2 = false; //stop searching to the right (diagonal right to left)
		for (int i=lastRow-1, j=lastColumn+1; i>=0 && j <columns && countLeftToRight < winningNumber && !stopRight1; i--, j++)
		{
			if (gameState[i][j] == player)
				countLeftToRight++;
			else
				stopRight1 = true;
			
		}
		if (countLeftToRight < winningNumber)
		{
			for (int i=lastRow+1, j=lastColumn-1; i<rows && j>=0 && countLeftToRight < winningNumber && !stopLeft1; i--, j--)
			{
				if (gameState[i][j] == player)
					countLeftToRight++;
				else
					stopLeft1 = true;
			}
		
		
			if (countLeftToRight < winningNumber)
			{
				for (int i=lastRow+1, j=lastColumn+1; i<rows && j<columns && countRightToLeft < winningNumber && !stopLeft2; i++, j++)
				{
					if (gameState[i][j] == player)
						countRightToLeft++;
					else
						stopLeft2 = true;
				}
		
				if (countRightToLeft < winningNumber)
				{
					for (int i=lastRow-1, j=lastColumn-1; i>=0 && j>=0 && countRightToLeft < winningNumber && !stopRight2; i--, j--)
					{
						if (gameState[i][j] == player)
							countRightToLeft++;
						else
							stopRight2 = true;
					}
				}
			}
		}
		if (countRightToLeft >= winningNumber || countLeftToRight >= winningNumber)
			winDiagonals = 1;
		
		return winDiagonals;
			
	}

	public void playGame()
	{
		
		int winner = 0;
		boolean gameOn = true;
		outputGameState();
		boolean invalidInput = true;
		System.out.println("Player "+player+"'s turn");
		while(invalidInput && gameOn)
		{
			System.out.println("Enter a column number between 1 and " + (columns));	
			//int colNumber = scanner.hasNextInt() ? Integer.parseInt(scanner.nextLine()) : 0;
			//System.out.println(colNumber);
			//scanner.next();
			try
			{
				int colNumber = Integer.parseInt(scanner.next());
				if (colNumber>=1 && colNumber<=columns)
				{
					
					if(!insertChip(player,colNumber))
						System.out.println("The column is already full.");
					else
						outputGameState();
					winner= detectWin();
					if (winner==1)
					{  
						System.out.println("Player " + player+" won");
						gameOn=false;
						
					}
					else if(isGameFull())
					{
						System.out.println("The game is tied");
						gameOn=false;
					}
					else
					{
						
						player=(player==1) ? 2 : 1;
						System.out.println("Player " + player + "'s turn");
					}		
				}
				else if (colNumber==-1)
				{
					gameOn=false;
				}
				else
					invalidInput = true;
			}
		
			catch (Exception e)
			{
				//System.out.println("In the catch block");
			}
			finally
			{
				//System.out.println("in the final block");		
			}
			
			}	
		}
	

	public static void main(String args[]) 
	{
		int rows = 6; 
		int columns = 7; 
		int winningNumber = 4;
		if(args.length == 3) 
		{
			
			//set rows, columns, and winningNumber to the input arguments
			rows=Integer.parseInt(args[0]);
			columns=Integer.parseInt(args[1]);
			winningNumber=Integer.parseInt(args[2]);
		}
		boolean keepPlaying = true;
		while(keepPlaying) 
		{
			ConnectN connectN = new ConnectN(rows, columns, winningNumber);
			connectN.playGame(); 
			//	boolean validInput = false;
			
			boolean valid = false;
			while(!valid)
			{
				System.out.println("Do you want to play again? Please enter y/n");
				String play = scanner.next();//ask if user wants to play again
				if (play.equals("y")||play.equals("n"))
				{
					valid=true;
					if(play.equals("y"))
					{
						keepPlaying=true;
						connectN.resetGame();
					}
					//	continue loop if he/she does
					else 
						keepPlaying=false;
				}
			}
		}
		scanner.close();
		System.out.println("Thanks for playing...Bye!");
	}
}


