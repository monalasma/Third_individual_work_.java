# Third_individual_work_.java
MAIN class:
```java
import java.util.Scanner;
public class Main {
    private static Scanner scanner = new Scanner(System.in);
    private static CheeseShop cheeseShop = new CheeseShop();
    public static void main(String[] args) {
        while (true){
            System.out.println("Welcome to Cheese Shop!");
            System.out.println("Press 1 to add Cheese: ");
            System.out.println("Press 2 to see all the Cheeses: ");
            System.out.println("Press 3 to remove a cheese from the list: ");
            System.out.println("Press 4 to exit the program: ");

            int choice = scanner.nextInt();
            if (choice == 1){
                addCheese();
            } else if(choice == 2){
                printCheese();
            } else if(choice == 3){
                removeCheese();
            } else if (choice == 4){
                System.exit(0);
            }else{
            System.out.println("Invalid choice");
            break;
            } 
        }
    }
        
    public static void addCheese(){
        System.out.println("Provide the cheese name: ");
        String name = scanner.next();
        System.out.println("Provide the cheese price: ");
        float price = scanner.nextInt();
        var cheese = new Cheese(name, price);
        cheeseShop.addCheese(cheese);
    }
    public static void printCheese(){
        System.out.println("These are the cheeses in the storage: ");
                var cheeses = cheeseShop.getCheese();
                for (var cheese : cheeses){
                    System.out.println(cheese.getName() + " with the price of " + cheese.getPrice());
                }
    }
    public static void removeCheese(){
        System.out.println("Provide the cheese name to remove: ");
        String name = scanner.next();
        cheeseShop.removeCheese(name);
    }
    
}
```
CheeseShop class:
```java
import java.util.ArrayList;
public class CheeseShop{

    private ArrayList <Cheese> cheeses = new ArrayList<Cheese>();

    public ArrayList <Cheese> getCheese(){
        return cheeses;
    }

    public void addCheese(Cheese cheese){
        cheeses.add(cheese);
    }

    public void removeCheese(String name){
        for(var cheese : cheeses){
            if(cheese.getName().equals(name)){
                cheeses.remove(cheese);
                return;
            }
        }
    }

    public void updateCheese(String name, int price){
        for (var cheese : cheeses){
            if(cheese.getName() == name){
                cheese.setName(name);
                cheese.setPrice(price);
                return;
            }
        }
    }

}
```
Cheese class:
```java
public class Cheese{
 private String name;
 private float price;

 public Cheese(String name, float price){
     this.name = name;
     this.price = price;
 }

 public void setName(String name){
     this.name = name;
 }
 public String getName(){
     return name;
 }
 public void setPrice (int price){
     this.price = price;
 }
 public float getPrice(){
     return price;
 }
}
```
