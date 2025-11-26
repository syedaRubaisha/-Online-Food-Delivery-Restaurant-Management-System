# -Online-Food-Delivery-Restaurant-Management-System

using System;
using System.Collections.Generic;

class Program
{
    static Dictionary<int, string> menu = new Dictionary<int, string>()
    {
        {1, "Burger - Rs 350"},
        {2, "Pizza - Rs 800"},
        {3, "Fries - Rs 150"}
    };

    static Dictionary<int, string> orderStatus = new Dictionary<int, string>();
    static int orderCounter = 0;

    static void Main()
    {
        while (true)
        {
            Console.WriteLine("\n--- ONLINE FOOD ORDERING SYSTEM ---");
            Console.WriteLine("1. Show Menu");
            Console.WriteLine("2. Place Order");
            Console.WriteLine("3. Track Order");
            Console.WriteLine("4. Exit");
            Console.Write("Enter choice: ");

            int choice = int.Parse(Console.ReadLine());

            switch (choice)
            {
                case 1:
                    ShowMenu();
                    break;
                case 2:
                    PlaceOrder();
                    break;
                case 3:
                    TrackOrder();
                    break;
                case 4:
                    return;
                default:
                    Console.WriteLine("Invalid option.");
                    break;
            }
        }
    }

    static void ShowMenu()
    {
        Console.WriteLine("\n--- MENU ---");
        foreach (var item in menu)
        {
            Console.WriteLine($"{item.Key}. {item.Value}");
        }
    }

    static void PlaceOrder()
    {
        ShowMenu();
        Console.Write("\nEnter item number: ");
        int choice = int.Parse(Console.ReadLine());

        if (menu.ContainsKey(choice))
        {
            orderCounter++;
            orderStatus[orderCounter] = "Order Placed";
            Console.WriteLine($"\nOrder ID {orderCounter} placed for {menu[choice]}");
        }
        else
        {
            Console.WriteLine("Invalid choice!");
        }
    }

    static void TrackOrder()
    {
        Console.Write("\nEnter Order ID: ");
        int id = int.Parse(Console.ReadLine());

        if (orderStatus.ContainsKey(id))
        {
            Console.WriteLine($"Order Status: {orderStatus[id]}");
        }
        else
        {
            Console.WriteLine("Order not found.");
        }
    }
}
