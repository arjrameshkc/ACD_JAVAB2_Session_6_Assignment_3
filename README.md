# ACD_JAVAB2_Session_6_Assignment_3
package Session6_Assignment;

public class BankingApplication {
	int accNum;
	String cusName;
	double currBal;
	double minAmt,depositAmt,withDrawAmt;
 
	public BankingApplication(int accNum, String cusName, double currBal, double minAmt, double depositAmt,
			double withDrawAmt) {
		super();
		this.accNum = accNum;
		this.cusName = cusName;
		this.currBal = currBal;
		this.minAmt = minAmt;
		this.depositAmt = depositAmt;
		this.withDrawAmt = withDrawAmt;
	}
	
	public synchronized void deposit(){
		System.out.println("Customer Account number:"+ " " +accNum);
		System.out.println("Customer Name:"+ " " +cusName);
		System.out.println("Customer Current balance  before adding:"+ " " +currBal);
		System.out.println("Deposit amount:"+ " " +depositAmt);		
	    currBal = currBal + depositAmt;
	    System.out.println("Customer Current balance  after deposit:"+ " " +currBal);			
			
 }
		
	public synchronized void withdraw()
	{
		System.out.println("Customer Account number:"+ " " +accNum);
		System.out.println("Customer Name:"+ " " +cusName);
		System.out.println("Customer Current balance  before withdraw:"+ " " +currBal);
		System.out.println("Withdraw amount:"+ " " +withDrawAmt);	
		if(withDrawAmt > currBal ){
			System.out.println("Available balance less then withdraw amount");			
		} 
		else if(currBal <= minAmt) {
			System.out.println("You  donot have sufficient balance to withdraw");
		}
		else {
			
			currBal = currBal - withDrawAmt;
			System.out.println("Customer Current balance  after withdrawn:"+ " " +currBal);
		}	    
	    	
	}
	
	}


12package Session6_Assignment;

import java.util.Scanner;
public class BankingApplicationMain {
	 
 public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner sc = new Scanner(System.in);	
		System.out.println(" Enter Customer Account number:");
		int accNum = sc.nextInt();
		System.out.println(" Enter Customer Name:");
		String cusName = sc.next();
		System.out.println("Customer Current balance:");
		double currBal = sc.nextDouble();
		System.out.println(" enter Deposit amount:");
		double depositAmt = sc.nextDouble();
		System.out.println(" enter withdraw amount:");
		double withDrawAmt = sc.nextDouble();
		double minAmt = 500.00; 
		BankingApplication ba = new BankingApplication(accNum,cusName,currBal,minAmt,depositAmt,withDrawAmt);
		Thread ThreadOne = new Thread(){
			public void run(){
				ba.deposit();
			}
			};
			Thread ThreadTwo = new Thread(){
				public void run(){
					ba.withdraw();
				}
				};
	ThreadOne.start();
	ThreadTwo.start();
	
 }
}
		

	

		
		
		

