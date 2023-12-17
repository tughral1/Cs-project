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

