// Dependency
#include <iostream>
#include <array>
#include <string>
#include <vector>



enum class options
{
    Fetch_Record=2,
    Add_Record=1,
    Quit=3
};


class person
{
    public:  //access modifier

    //nouns --> (name - age)
    std::string name;
    int age;

    //default person 
    person():name(""), age(0) {};
    
    //initialized constructor
    person(std::string n, int a): name (n), age (a) {};

    // functionality
    void Display()
    {
        std::cout << "\nName: " << name << "\n";
        std::cout << "Age: " << age << "\n\n";
    }
};

// Definning array of class person
std::array<person,100> Container;

// Definning a vector of person called records
std::vector<person> records;

constexpr int MAX_RECORD_SIZE= 100;
constexpr int MIN_RECORD_SIZE= 0;
options defualt_option= options::Add_Record;


void AddRecord ( std::string name1, int age1)
{
    if (records.size() < MAX_RECORD_SIZE)
    {
        records.emplace_back(name1, age1 );
        std::cout << "\nUser recorded added successfully. \n\n";
    }
    else 
        std::cout << "Can't add more records\n"
                  << "Maximum recorded size has been reaced\n";

}


person FetchRecord(const int ID)
{
    if( ID >=MIN_RECORD_SIZE &&  ID <= MAX_RECORD_SIZE )
        {
            return records[ID];
        }

    else 
        std::cout << "Invalid ID. \n";
        return person();

}


// operator >> overloading to input user defined option
std::istream& operator>> (std::istream & input_stream, options& result )
{
    int op;
    input_stream >> op;
    result= static_cast<options>(op);
    return input_stream;
}


options selected = defualt_option;

int main ()
{
    std::cout<< "User SignUp Application\n\n";
    
     
    while (selected != options::Quit)
    {   std::cout << "Please select an option: \n";
        std::cout << "1: Add Record \n"
                  << "2: Fetch Recoed \n"
                  << "3: Quit \n\n";

        std::cout << "Enter Option: ";
        std::cin >> selected;

        std::string temp_name;
        int temp_age=0;
        person p ;

        switch (selected)
        {

        case options::Add_Record :


            std::cout << "Add User. Please user name and age\n" ;

            std::cout << "Name: " ;
            std::cin.ignore(); //To ignore the newline char in the previos buffer 
            std::getline(std::cin , temp_name); // to get string more than one word
            std::cout << "Age: " ;
            std::cin >> temp_age;
            AddRecord(temp_name,temp_age);
        break;
        
        case options::Fetch_Record :

            int temp_ID;
            std::cout << "Please enter user ID: " ;
            std::cin >> temp_ID;
            p = FetchRecord(temp_ID);
            p.Display();
            
        break; 
        case options::Quit :
            selected=options::Quit;
         break;
        default:
            std::cout << "Invalid Option.\n";
            selected=options::Quit;
            break;
        }
    
    }
    
    return 0;
}

