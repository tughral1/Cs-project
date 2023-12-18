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
void data_display(vector<string> name, vector<int> reg_no, vector<string> faculty, vector<string> contact_no){
    
    cout<<endl;
    for(int i = 0; i < 26; i++){
            cout<<char(178);
        }
        cout<<endl;    
        
    for(int i = 0; i < name.size(); i++){
        cout<<"Student Name "<<i+1<<" : "<<name[i]<<endl;
        cout<<"Registration # "<<" "<<reg_no[i]<<endl;
        cout<<"Faculty : "<<faculty[i]<<endl;
        cout<<"Contact no : "<<contact_no[i]<<endl;
        for(int i = 0; i < 26; i++){
            cout<<char(178);
        }
        cout<<endl;

    }    
}
void initialisation(vector<string> &name, vector<int> &reg_no, vector<string> &faculty, vector<string> &contact_no){
  ifstream name_file ("name.txt");
  string line;
  while(getline(name_file, line)){
    name.push_back(line);
  }
  name_file.close();

  ifstream reg_file("reg_no.txt");
  int no;
  while(reg_file >> no){
    reg_no.push_back(no);
  }
  reg_file.close();

  ifstream contact_file("contact_no.txt");
  while(contact_file >> line){
    contact_no.push_back(line);
  }
contact_file.close();

  ifstream faculty_file("faculty.txt");
  while(faculty_file >> line){
    faculty.push_back(line);
  }
  faculty_file.close();
}

void record_updation(vector<string> &name, vector<int> &reg_no, vector<string> &faculty, vector<string> &contact_no){
  
  ofstream name_file("name.txt");
  for(int i = 0; i < name.size(); i++){
    name_file<<name[i]<<endl;
  }
  name_file.close();

  ofstream reg_file("reg_no.txt");
  for(int i = 0; i < reg_no.size(); i++){
    reg_file<<reg_no[i]<<endl;
  }
  reg_file.close();

  ofstream faculty_file("faculty.txt");
  for(int i = 0; i < faculty.size(); i++){
    faculty_file<<faculty[i]<<endl;
  }
  faculty_file.close();

  ofstream contact_file("contact_no.txt");
  for(int i = 0; i < contact_no.size(); i++){
    contact_file<<contact_no[i]<<endl;
  }
  contact_file.close();
}
void enter_data(vector<string> &name, vector<int> &reg_no, vector<string> &faculty, vector<string> &contact_no){
    string t_name;
    int t_reg;
    string t_faculty;
    string t_contact_no;
    int size;
    

    cout<<"How many students do you want to enter : \n";
    cin>>size;

    cout<<endl;

    for (int i = 0; i < size; i++){
        cout<<"Enter name of student#"<<i+1<<" : "<<endl;
        getline(cin>> ws,  t_name);
        name.push_back(t_name);
        cout<<"Enter Registration no of student"<<i+1<<" : "<<endl;
        cin>>t_reg;
        reg_no.push_back(t_reg);
        cout<<"Enter faculty of student"<<i+1<<" : "<<endl;
        cin>>t_faculty;
        faculty.push_back(t_faculty);
        cout<<"Enter contact no of student"<<i+1<<" : "<<endl;
        cin>>t_contact_no;
        contact_no.push_back(t_contact_no);
        cout<<endl;
    }
}

int main(){
    char save;
    int choice;
    int size;
    vector<string> name;
    vector<int> reg_no;
    vector<string> faculty;
    vector<string> contact_no;

    initialisation(name, reg_no, faculty, contact_no);

do{
    cout<<endl;
    cout<<"*****************STUDENT MANAGEMENT SYSTEM***************\n\n";
    cout<<"1. Data Entry \n";
    cout<<"2. Data display \n";
    cout<<"3. Search and Update \n";
    cout<<"4. Delete student record \n";
    cout<<"5. Exit and Save Changes \n\n";

    cout<<"Enter function : \n";
    cin>>choice;
    
    switch(choice){
        case 1:
           enter_data(name, reg_no, faculty, contact_no);
        break;

        case 2 :
           data_display(name, reg_no, faculty, contact_no);
           break;

        case 3:
           update_data(name, reg_no, faculty, contact_no);
           break;

        case 4:
           del(name, reg_no, faculty, contact_no);
           break;

        case 5:
           break;
              
        default:
           cout<<"Invalid Function!\n";  
    }

}while(choice != 5);
cout<<endl;

cout<<"Do you want to save the changes (y/n) : \n";
cin>>save;
save = toupper(save);
cout<<endl;

if(save == 'Y'){
    record_updation(name, reg_no, faculty, contact_no);
    cout<<"Changes saved succesfully!\n";
}
cout<<endl;
cout<<"************SAYONARA**************\n";  
}



