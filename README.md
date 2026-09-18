# Restaurant-ordering-system-
We created a code for the restaurant that includes the menu, offers discount cards, and different payment methods.


#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

template <class T>
void printData(T data)
{
    cout << data << endl;
}

class Food
{
protected:
    string name;
    double price;

public:
    Food(string n, double p) : name(n), price(p) {}

    virtual void display()
    {
        cout << name << " - AED " << price << endl;
    }

    string getName() { return name; }
    double getPrice() { return price; }
};

class Appetizer : public Food
{
public:
    Appetizer(string n, double p) : Food(n, p) {}
};

class MainDish : public Food
{
public:
    MainDish(string n, double p) : Food(n, p) {}
};

class Dessert : public Food
{
public:
    Dessert(string n, double p) : Food(n, p) {}
};

class Drink : public Food
{
public:
    Drink(string n, double p) : Food(n, p) {}
};

int main()
{
    try
    {
        string customer, phone;

        cout << "===== Shahad & Mariam Restaurant =====" << endl;

        cout << "Enter Customer Name: ";
        getline(cin, customer);

        cout << "Enter Phone Number: ";
        getline(cin, phone);

        // MAIN DISHES
        MainDish pasta("pasta", 18);
        MainDish pizza("pizza", 25);
        MainDish steak("steak", 40);

        // APPETIZERS
        Appetizer fries("frenchfries", 10);
        Appetizer bread("garlicbread", 8);
        Appetizer salad("salad", 12);

        // DESSERTS
        Dessert cake("cake", 15);
        Dessert icecream("icecream", 10);
        Dessert datecake("datecake", 14);

        // DRINKS
        Drink juice("orangejuice", 7);
        Drink pepsi("pepsi", 5);
        Drink water("water", 2);

        Food* order[20];
        int count = 0;
        string food;

        cout << "\n===== MENU =====" << endl;

        cout << "\nMAIN DISHES\nPasta - 18\nPizza - 25\nSteak - 40" << endl;
        cout << "\nAPPETIZERS\nFrenchFries - 10\nGarlicBread - 8\nSalad - 12" << endl;
        cout << "\nDESSERTS\nCake - 15\nIceCream - 10\nDateCake - 14" << endl;
        cout << "\nDRINKS\nOrangeJuice - 7\nPepsi - 5\nWater - 2" << endl;

        cout << "\nType Finish to finish ordering." << endl;

        do
        {
            cout << "\nEnter Food and Drink: ";
            cin >> food;

            transform(food.begin(), food.end(), food.begin(), ::tolower);

            if (food == "pasta") { order[count++] = &pasta; cout << "✔ Order added successfully" << endl; }
            else if (food == "pizza") { order[count++] = &pizza; cout << "✔ Order added successfully" << endl; }
            else if (food == "steak") { order[count++] = &steak; cout << "✔ Order added successfully" << endl; }

            else if (food == "frenchfries") { order[count++] = &fries; cout << "✔ Order added successfully" << endl; }
            else if (food == "garlicbread") { order[count++] = &bread; cout << "✔ Order added successfully" << endl; }
            else if (food == "salad") { order[count++] = &salad; cout << "✔ Order added successfully" << endl; }

            else if (food == "cake") { order[count++] = &cake; cout << "✔ Order added successfully" << endl; }
            else if (food == "icecream") { order[count++] = &icecream; cout << "✔ Order added successfully" << endl; }
            else if (food == "datecake") { order[count++] = &datecake; cout << "✔ Order added successfully" << endl; }

            else if (food == "orangejuice") { order[count++] = &juice; cout << "✔ Order added successfully" << endl; }
            else if (food == "pepsi") { order[count++] = &pepsi; cout << "✔ Order added successfully" << endl; }
            else if (food == "water") { order[count++] = &water; cout << "✔ Order added successfully" << endl; }

            else if (food != "finish")
                cout << "Not Available In Our Restaurant!" << endl;

        } while (food != "finish");

        if (count == 0)
            throw "No Order Found!";

        double total = 0;

        cout << "\n===== YOUR ORDER =====" << endl;

        for (int i = 0; i < count; i++)
        {
            order[i]->display();
            total += order[i]->getPrice();
        }

        double originalTotal = total;

        char discount;
        cout << "\nDo You Have Discount Card? (Y/N): ";
        cin >> discount;

        if (discount == 'Y' || discount == 'y')
        {
            double finalTotal = total * 0.8;

            cout << "\n===== DISCOUNT INFO =====" << endl;
            cout << "Original Total: AED " << originalTotal << endl;
            cout << "Discount: 20%" << endl;
            cout << "Final Total: AED " << finalTotal << endl;

            total = finalTotal;
        }

        string payment;
        cout << "\nPayment Method (Cash/Card): ";
        cin >> payment;

        cout << "\n===== BILL =====" << endl;
        cout << "Customer: " << customer << endl;
        cout << "Phone: " << phone << endl;
        cout << "Payment: " << payment << endl;
        cout << "Total: AED " << total << endl;

        cout << "\nThank you for visiting our restaurant." << endl;
    }
    catch (const char* error)
    {
        cout << "Error: " << error << endl;
    }

    return 0;
}
