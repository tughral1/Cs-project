# Cs-project
#include <iostream>
#include <string>
#include <vector>
#include <fstream>
using namespace std;

void del(vector<string> &name, vector<int> &reg_no, vector<string> &faculty, vector<string> &contact_no){
    
    int t_reg;
    int index;
    bool rec = false;
    cout<<endl;
    cout<<"Enter reg_no of the student record you want to delete : \n";
    cin>>t_reg;
    for(int i = 0; i < reg_no.size(); i++){
        if (t_reg == reg_no[i]){
            rec = true;
            index = i;
        }   
    }
    if(rec == true){

        contact_no.erase(contact_no.begin() + (index));
        reg_no.erase(reg_no.begin() + (index));
        name.erase(name.begin() + (index));
        faculty.erase(faculty.begin() + (index));

        contact_no.shrink_to_fit();
        reg_no.shrink_to_fit();
        name.shrink_to_fit();
        faculty.shrink_to_fit();
   cout<<"Record was succesfully deleted!\n";
    }
    else{
        cout<<"This record doesn't exist!\n";
    }
}

void update_data(vector<string> &name, vector<int> &reg_no, vector<string> &faculty, vector<string> &contact_no){
    
    int t_reg;
    char choice;
    int change_choice;
    bool rec = false;
    int index;
    string temp;
    int r_temp;
    
    cout<<endl;
    cout<<"Enter the registration number of the student : \n";
    cin>>t_reg;
    for(int i = 0; i < reg_no.size(); i++){
        if (t_reg == reg_no[i]){
            rec = true;
            index = i;
            cout<<endl;
            cout<<"Student Name : "<<name[i]<<endl;
            cout<<"Registration# : "<<reg_no[i]<<endl;
            cout<<"faculty"<<" : "<<faculty[i]<<endl;
            cout<<"Contact no : "<<contact_no[i]<<endl;
            cout<<endl;
            break;
        }
    }
    if(rec){
        cout<<"Do you want to edit the record of this student (y/n) : \n";
        cin>>choice;
        choice = toupper(choice);
        
        if (choice == 'Y'){
            cout<<endl;
            cout<<"Which field would you like to add changes to : \n";
            cout<<"1. Name \n";
            cout<<"2. Registration # \n";
            cout<<"3. Faculty \n";
            cout<<"4. Contact no \n";
            cin>>change_choice;
            cout<<endl;

            switch(change_choice){
                case 1:
                   cout<<"Enter name : ";
                   getline(cin >> ws, temp);
                   name[index] = temp;
                   cout<<"Changes made succesfully!\n";
                   cout<<endl;
                   break;

                case 2:
                   cout<<"Enter Registration # : ";
                   cin>>r_temp;
                   reg_no[index] = r_temp;
                   cout<<"Changes made succesfully!\n";
                   cout<<endl;
                   break;

                case 3:
                   cout<<"Enter faculty : ";
                   cin>>temp;
                   faculty[index] = temp;
                   cout<<"Changes made succesfully!\n";
                   cout<<endl;
                   break;

                case 4:
                   cout<<"Enter Contact no : ";
                   cin>>temp;
                   contact_no[index] = temp;
                   cout<<"Changes made succesfully!\n";
                   cout<<endl;
                   break;

                default:
                   cout<<"Invalid Field!\n";       

            }
        }    
    }
    else{
        cout<<endl;
        cout<<"This record doesn't exist!\n";
    }

}

