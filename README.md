# LBYEC72-EB1_SY_TE
#include<stdio.h>
#include<string.h>
#include <stdlib.h>
#include <iostream>

using namespace std;

typedef struct classes{
	char subject[10];
	int time;
	int endtime;
}classes;

int main(){
	int choice, classcount, timecheck, endtimecheck, highervalueendtime;
	classes myclass[50];
	classcount = 0;
	cout<<"\n||||||  ADMIN MENU  ||||||\n";
	while(choice != 5){
	cout<<"Choose From The Following:\n\n";
	cout<<"1. Add a Course\n";
	cout<<"2. Remove a Course\n";
	cout<<"3. View The Courses Available\n";
	cout<<"4. Save the Courses Already Offered\n";
	cout<<"5. Exit the Program\n";
	cin>>choice;
		
		switch(choice){
			
			case 1: cout<<"\n\n ----- Add A Class -----\n\n";{
				
				if (classcount < 10){
					cout<<"Class Code: ";
					cin>>myclass[classcount].subject;
					cout<<"\nClass Time: ";
					cin>>timecheck;
					cout<<"Class End Time: ";
					cin>>endtimecheck;
					
					if( (timecheck < 7) || ( timecheck >20)){
						cout<<"\n      *****Invalid Time*****\n";
						cout<<" --- Class Is Not In Class Hours ---\n\n";
						classcount--;
					}
					
					else if(endtimecheck > 21){
						cout<<"\n      *****Invalid Time*****\n";
						cout<<" --- Class Is Not In Class Hours ---\n\n";
						classcount--;
					}
					
					else if( (endtimecheck - timecheck) > 3){
						cout<<"\n      *****Invalid Time*****\n";
						cout<<"    --- Invalid Time Duration ---\n\n";
						classcount--;
					}
					
					else{
						myclass[classcount].time = timecheck;
						myclass[classcount].endtime = endtimecheck;
					}
					
					
				
					classcount++;						
					int w, u, highervalue;
					char copy[10];	
						for(w= 0; w < classcount; w++){
							for(u = w + 1; u < classcount; u++){
								if(myclass[w].time > myclass[u].time){
									highervalue = myclass[w].time;
									highervalueendtime = myclass[w].endtime;
									strcpy(copy,myclass[w].subject);
									myclass[w].time = myclass[u].time;
									myclass[w].endtime = myclass[u].endtime;
									strcpy(myclass[w].subject,myclass[u].subject);
									myclass[u].time = highervalue;
									strcpy(myclass[u].subject,copy);
									myclass[u].endtime = highervalueendtime;
								}
							}
						}
					break;
				}
				
				else
					cout<<"  ***** SCHEDULE FULL *****\n";
					cout<<"   --- Cannot Add Class ---\n\n";
					break;
			}
			
			case 2: cout<<"\n\n     ----- Remove A Class ----- \n\n";{
				int i, remove;
					if(classcount == 0){
						cout<<"  ***** Cannot Remove A Class *****\n\n";
						cout<<"   ----- Schedule is Empty -----   \n\n";
						break;
					}
					else{
						cout<<" No. | Class Time Slot | Class Name\n";
						cout<<"-----------------------------------\n";
							for(i = 0; i < classcount ; i++){
						
							if(myclass[i].time < 9){	
								if((myclass[i].time < 9) && (myclass[i].endtime > 9)){
								cout<<  i+1  <<" |    0" << myclass[i].time <<"00  -  "<<myclass[i].endtime<<"00   |"<<myclass[i].subject<<"  \n";
							
								}
								else
								cout<<  i+1  <<" |    0" << myclass[i].time <<"00  -  0" <<myclass[i].endtime<<"00   |"<<myclass[i].subject<<"  \n";	
								
							}	
							else if(myclass[i].time == 9){
								cout<<  i+1  <<" |    0" << myclass[i].time <<"00  -  " <<myclass[i].endtime<<"00   |"<<myclass[i].subject<<"  \n";
								
							
							}

							else{
									if(i+1 == 10)
									{
				cout<<  i+1  <<" |    " << myclass[i].time <<"00  -  " <<myclass[i].endtime<<"00   |"<<myclass[i].subject<<"  \n";
										
									}
									else
				cout<<  i+1  <<" |    " << myclass[i].time <<"00  -  " <<myclass[i].endtime<<"00   |"<<myclass[i].subject<<"  \n";
								}
							}
					}
						
					cout<<"\nChoose A Class To Remove: \n";
					cin>>remove;
					
					if( (remove < 0) || (remove > classcount)){
						cout<<"\n    ***** Invalid Input ***** \n";
						cout<<"--- Choice Is Not Among Options --- \n\n";
						break;
					}
					else{
					
					int j;
					
					for(j = remove -1; j < classcount; j++){
					strcpy(myclass[j].subject, myclass[j + 1].subject);
					myclass[j].time = myclass[j + 1].time;
					myclass[j].endtime = myclass[j + 1].endtime;
					}
					classcount--;
					break;
				}
			}
			
			
			case 3: cout<<"\n\n ----- View The Courses Already Offered ---- \n\n";{
				int i;
				if(classcount == 0){
					cout<<"  ***** Cannot View Schedule *****\n";
					cout<<"    --- You Have No Classes ---\n\n";
				}
				
				else{
				cout<<" No. | Class Time Slot | Class Name\n";
				cout<<"-----------------------------------\n";
					for(i = 0; i < classcount ; i++){
						
							if(myclass[i].time < 9){	
								if((myclass[i].time < 9) && (myclass[i].endtime > 9)){
									cout<<  i+1  <<" |    0" << myclass[i].time <<"00  -  "<<myclass[i].endtime<<"00   |"<<myclass[i].subject<<"  \n";
								
								}
								else
									cout<<  i+1  <<" |    0" << myclass[i].time <<"00  -  0" <<myclass[i].endtime<<"00   |"<<myclass[i].subject<<"  \n";
								
							}	
							else if(myclass[i].time == 9){
									cout<<  i+1  <<" |    0" << myclass[i].time <<"00  -  " <<myclass[i].endtime<<"00   |"<<myclass[i].subject<<"  \n";
								
							
							}
							
							else{
									if(i+1 == 10)
									{
									cout<<  i+1  <<" |    " << myclass[i].time <<"00  -  " <<myclass[i].endtime<<"00   |"<<myclass[i].subject<<"  \n";
										
										
									}
									else
									cout<<  i+1  <<" |    " << myclass[i].time <<"00  -  " <<myclass[i].endtime<<"00   |"<<myclass[i].subject<<"  \n";
										
								}
					}
				}
				break;
			}
			case 4: cout<<"\n ----- Save Courses Offered -----\n";{
					cout<<"   ---Courses Saved---\n\n";
					cout<<"***Check AdminCourses.Txt File***\n\n";
				int i;
				FILE *f = fopen("AdminCourses.txt", "w");
				fprintf(f," No. | Class Time Slot | Class Name\n");
				fprintf(f,"-----------------------------------\n");
					for(i = 0; i < classcount ; i++){
						
						if(myclass[i].time < 9){
								if((myclass[i].time < 9) && (myclass[i].endtime > 9)){
								fprintf(f,"  %d  |   0%d00 - %d00   |    %s \n", i + 1, myclass[i].time, myclass[i].endtime, myclass[i].subject );
								}
								else	
								fprintf(f,"  %d  |   0%d00 - 0%d00   |    %s \n", i + 1, myclass[i].time, myclass[i].endtime, myclass[i].subject );
						}
						else if(myclass[i].time == 9){
							fprintf(f,"  %d  |   0%d00 - %d00   |    %s \n", i + 1, myclass[i].time, myclass[i].endtime, myclass[i].subject );
							
						}
						
						else{
							if(i+1 == 10)
								{
								fprintf(f," %d  |   %d00 - %d00   |    %s \n", i + 1, myclass[i].time, myclass[i].endtime, myclass[i].subject );
								}
							else
								fprintf(f,"  %d  |   %d00 - %d00   |    %s \n", i + 1, myclass[i].time, myclass[i].endtime, myclass[i].subject );
						}
					}
					fclose(f);
				
				
				break;
			}
			
			case 5: printf("---- Exit Program ----"); {
				break;
			}
		}
	}
}

