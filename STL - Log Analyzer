// Wrriten by: Muhammad Asad Naveed
// U.No: 3035957848
// Assignment 3 Question 2
// Description: Complete the program and the program will read and process a web log 
                //data file from user input (cin). The program will then print out the 
                //5 most popular pages, and the 5 most active users and the corresponding pages they have visited.

#include<iostream>
#include<algorithm>
#include<string>
#include<map>
#include<vector>

using namespace std;

struct Page {
    int id;
    string path;
    int counter;
    Page(int id, string path) {
        this->id = id;
        this->path = path;
        counter = 0;
    };
};

// This function can facilitate sorting
bool operator<(const Page & a, const Page & b) {
    return (a.id < b.id);
}

vector<Page> pages;

struct User {
    int id;
    vector<string> visits;
    User(int id) {
        this->id = id;
    };
    void add_visit(int page_id) {
        Page p(page_id, "");
        vector<Page>::iterator iter = lower_bound(pages.begin(), pages.end(), p);
        if(iter->id == page_id)
            visits.push_back(iter->path);
    };
    int size() const {
        return visits.size();
    };
    void print_visits() {
        sort(visits.begin(), visits.end());
        vector<string>::iterator iter;
        for(iter = visits.begin(); iter != visits.end(); iter++) {
            cout << "- " << *iter << endl;
        }
    }
};

vector<User> users;

// function to facilitate the sorting of users
bool operator<(const User & a, const User & b) 
{

    if (a.size() == b.size())            //if size equal lexographical sorting done
    {
        return (a.id < b.id);
    }
    
    return (a.size() > b.size());         

        

}

// adds a page to the end of the pages vector
void add_page(const Page& p) {

    pages.push_back(p);

    

}

// for sorting
bool cmp_page_count(const Page & a, const Page & b) {

    if ( a.counter == b.counter )
    {
        return ( a.path < b.path );   // lexigraphical sorting if same number of times 
    }
    

    return ( a.counter > b.counter );   // sorting with the most popularity


}

// Prints the top 5 number of pages and the corresponding path
void print_pages(int number) {

    for ( int i = 0; i < number; i++ )
    {
        cout << pages[i].counter << ":" << pages[i].path << endl;
    }
}    

// adding user to the end of the vector users
void add_user(User u) {

    users.push_back(u);               //the record is added at the end

}

// adds the path that the user visited
void add_visit(int page_id) {

    vector<Page>::iterator itr;

    for (itr = pages.begin() ; itr != pages.end(); itr++)
    {
        if (itr->id == page_id )
        {
            users.back().visits.push_back(itr->path);
            itr->counter++;
            break;
        }
    }

}

// Prints the top 5 users, their id and the  page path
void print_users(int number) 
{

    for (int x = 0; x < number; x++)
    {
        cout << users[x].size() << ':' << users[x].id << endl;
        users[x].print_visits();                                 //prints pages that the user visited
    }



}


// this is the main function
int main() {

    string type;
    while(cin >> type) {
        if(type == "USER") {
          int user_id;
          cin >> user_id;
          User u(user_id);
          add_user(u);
        } else if(type == "PAGE") {
          int page_id;
          string page_path;
          cin >> page_id;
          cin >> page_path;
          Page p(page_id, page_path);
          add_page(p);
        } else if(type == "VISIT") {
          int page_id;
          cin >> page_id;
          Page p(page_id, "");
          
          add_visit(p.id);
        }
    }
    sort(pages.begin(), pages.end(), cmp_page_count);
    cout << "*** 5 most popular pages ***" << endl;
    print_pages(5);
    sort(pages.begin(), pages.end());

    sort(users.begin(), users.end());
    cout << "*** 5 most active users ***" << endl;
    print_users(5);

    return 0;

}
