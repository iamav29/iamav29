- 👋 Hi, I’m @iamai29
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
iamav29/iamav29 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
package dino_game;
import java.util.Random;
import java.util.Scanner;

public class battle {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int user, comp;
		int userattack,userdefense, compattack, compdefense;
		Scanner sc = new Scanner(System.in);
		Random rand = new Random();

		
		System.out.println("Pick a Dino:\n1 - T-Rex:\n" + 
				"Health: 20 pts\n" + 
				"Damage:\n" + 
				"Aggressive: 6 - 10\n" + 
				"Defensive: 4 - 8\n" + 
				"Defense:\n" + 
				"Aggressive: 0 - 2\n" + 
				"Defensive: 3 - 5\n\n" + 
				"2 - Stego:\n" + 
				"Health: 40 pts\n" + 
				"Damage:\n" + 
				"Aggressive: 3 - 6\n" + 
				"Defensive: 1 - 4\n" + 
				"Defense:\n" + 
				"Aggressive: 1 - 3\n" + 
				"Defensive: 4 - 8\n\n" + 
				"3 - Triceratops:\n" + 
				"Health 30 points\n" + 
				"Damage:\n" + 
				"Aggressive: 4 - 8\n" + 
				"Defensive: 2 - 6\n" + 
				"Defense:\n" + 
				"Aggressive: 1 - 4\n" + 
				"Defensive: 2 - 6\n" + 
				"");
		user = sc.nextInt();					
		
		
		dino u = new dino ();
		dino c = new dino();
		
		comp = rand.nextInt(3-1+1)+1;

		switch (user)
		{
		case 1:
			 u  = new dino("T-Rex",6,0,10,2,4,3,8,5,20);
		case 2:
			u = new dino("Stego",3,1,6,3,1,4,4,8,40);
		case 3: 
			u = new dino("Triceratops",4,1,8,4,2,2,6,6,30);
		}
		switch (comp)
		{
		case 1:
			 c  = new dino("T-Rex",6,0,10,2,4,3,8,5,20);
		case 2:
			c = new dino("Stego",3,1,6,3,1,4,4,8,40);
		case 3: 
			c = new dino("Triceratops",4,1,8,4,2,2,6,6,30);
		}
		
		int userturn = rand.nextInt(2-1+1)+1;
		System.out.println(userturn);
		int compturn;
		do 
		{
			System.out.println(c);
			System.out.println(u);

			if (userturn ==1)
			{
				System.out.println("It's Your Turn to Attack\nSelect:\n"
						+ "1 - Agressive\n"
						+ "2 - defensive");
				int userattacktype = sc.nextInt();
				
				int compattacktype = rand.nextInt(2-1+1)+1;
				 userattack = u.getattack(userattacktype);
				 userdefense = u.getdefense(userattacktype);
				 compattack = c.getattack(userattacktype);
				 compdefense = c.getdefense(userattacktype);

				c.adjusthealth(userattack, compdefense);
				u.adjusthealth(compattack, userdefense);
				
			}
			else if (userturn==2)
			{

				System.out.println("The CPU is Attacking!");
				int compattacktype = rand.nextInt(2-1+1)+1;
				System.out.println("Select:\n"
						+ "1 - Agressive\n"
						+ "2 - defensive");
				int userattacktype = sc.nextInt();
				 userattack = u.getattack(userattacktype);
				 userdefense = u.getdefense(userattacktype);
				 compattack = c.getattack(userattacktype);
				 compdefense = c.getdefense(userattacktype);	
				 u.adjusthealth(compattack, userdefense);
				 c.adjusthealth(userattack, compdefense);

				
			}
			
			if (userturn ==1)
			{
				user =comp;
			}
			else if (userturn ==2)
			{
				comp=user;
			}
			
		}while (u.gethealth() != 0 || c.gethealth()!=0);
		
		if (u.gethealth()==0)
		{
			System.out.println("Sorry You Lose");
		}
		
		else
		{
			System.out.println("Congrats You Won!");
		}
		
		sc.close();
	}

}
