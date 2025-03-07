#include<stdio.h>
#include<string.h>
#define maxdoc 100
#define maxpat 100
#define maxapp 100;
int n;
int b=0,z=0,m=0;
int d_count=0;
int p_count=0;

struct doctor{
    char name[90];
    char speaciality[90];
    int experience;
    int is_available;

    }d[maxdoc];
struct patient{
    char name[90];
    char disease[90];
    int age;
    int total_test;
    int consultationfee;
    int stay_cost;
    int total_bill;
}p[maxpat];
struct appointment{
    struct patient p;
    char doc_name[100];
    char date[100];
}a[100];
struct test {
    char test[30]; 
    int cost;
} t[100] = {
    {"x-ray", 500},
    {"blood-test", 1000},
    {"urine_test", 300},
    {"typhoid-test", 570},
    {"liquid-profile-test", 900},
    {"CBC", 850},
    {"BP-measurement", 150}
};

void add_doctor(){
    printf("enter number of doctors:");
    scanf("%d",&d_count);
  
    for(int i=b;i<b+d_count;i++){
        printf("enter the name of the doctor %d:",(i+1));
        scanf("%s",&d[i].name);
        printf("enter doctor %d speaciality:",(i+1));
        scanf("%s",&d[i].speaciality);
        printf("enter doctor %d experience:",(i+1));
        scanf("%d",&d[i].experience);
        d[i].is_available=1;
        

        printf("doctor added successfully\n");
    }
    b+=d_count;
    
}
void view_doctor(){
    printf("Doctors list:\n");

    for(int i=0;i<b;i++){
        //doctor list
        //name      |spl        |exp
        printf("%d.name:  %s  | speciality:  %s |  experience:  %d\n",(i+1),d[i].name,d[i].speaciality,d[i].experience);
        }
        z=d_count;
}
void add_patient(){
    printf("enter number of patients\n");
    scanf("%d",&p_count);
    for(int i=m;i<m+p_count;i++){
        printf("enter the name of the patient %d:",(i+1));
        scanf("%s",&p[i].name);
        printf("enter patient %d disease:",(i+1));
        scanf("%s",&p[i].disease);
        printf("enter patient %d age:",(i+1));
        scanf("%d",&p[i].age);
        printf("patient added successfully\n");
        p[i].total_test=0;

    }
    m+=p_count;
}
void view_patient(){
    printf("patients list:\n");
    for(int i=0;i<m;i++){
        printf(" %d.name : %s  |disease : %s  |age:  %d\n",(i+1),p[i].name,p[i].disease,p[i].age);
    }
}
void schedule_appointment(){
    printf("enter patient name:");
    char pname[100];
    char doct_name[100];
    scanf("%s",&pname);
    for(int i=0;i<p_count;i++){

        if(strcmp(p[i].name,pname)==0){
            char date[100];
            printf("Enter Appointment Date:");
            scanf("%s",&date);
            strcpy(a[i].date,date);
            strcpy(a[i].p.name,pname);
            printf("Available Doctors:\n");
            for(int j=0;j<d_count&&d[j].is_available!=0;j++){
                printf("%d.%s|Speacialization:%s|Experience:%d years\n",(j+1),d[j].name,d[j].speaciality,d[j].experience);
                }
            printf("Assign doctor:");
            scanf("%s",&doct_name);
            for(int j=0;j<d_count&&d[j].is_available!=0;j++){
            if(strcmp(doct_name,d[i].name)==0){
                strcpy(a[i].doc_name,doct_name);
                d[i].is_available=0;
                p[i].consultationfee=1000;
                printf("Appointment Scheduled Successfully\n");
                break;
                }
            }
        }else{
        printf("invalid patient");
        }
    }
}

void view_appointments(){
    printf("sceduled appointments are:\n");
    for(int i=0;i<p_count;i++){
        printf("Patient Name:%s|Doctor Name:%s|Date:%s\n",a[i].p.name ,a[i].doc_name,a[i].date);
    }

}
void view_tests(){
    printf("available tests:\n");
    for(int i=0;i<7;i++){
        printf("%d.test name: %s cost : %d\n",(i+1),t[i].test,t[i].cost);
    }
}
void assign_tests() {
    int k;
    char ch;
    char p_name[100];
    printf("Enter patient name: ");
    scanf("%s", p_name);
    int found = 0;
    for (int i = 0; i < p_count; i++) {
        if (strcmp(p[i].name, p_name) == 0) {
            found = 1;
            do {
                printf("Select from below:\n");
                for (int j = 0; j < 7; j++) {
                    printf("%d. Test name: %s | Cost: %d\n", (j + 1), t[j].test, t[j].cost);
                }
                printf("Enter the test number to assign to patient %s: ", p[i].name);
                scanf("%d", &k);

                
                if (k < 1 || k > 7) {
                    printf("Invalid test number. Please try again.\n");
                    continue;
                }

                printf("Test assigned: %s\n", t[k - 1].test);
                p[i].total_test += t[k - 1].cost;

                printf("Assign another test? (y/n): ");
                scanf(" %c", &ch);
            } while (ch == 'y' || ch == 'Y');

            printf("Tests assigned successfully!\n");
            break;
        }
    
    if (!found) {
        printf("Patient not found!\n");
    }
    }

}

void generate_bill(){
    char p_name[100];
    int stay;
    int total;
        for(int i=0;i<p_count;i++){
        printf("enter the name of the patient:");
        scanf("%s",&p_name);
        if(strcmp(p[i].name,p_name)==0){
            printf("enter the number of days for stay:");
            scanf("%d",&stay);
            printf("Final bill for %s\n",p[i].name);
            printf("consultation fee:%d\n",p[i].consultationfee);
            printf("test cost:%d\n",p[i].total_test);
            printf("hospital stay charge:%d\n",stay*400);
            total=p[i].consultationfee+p[i].total_test+stay*400;
            printf("Total Bill:%d\n",total);
            }
    }


}
int main(){
    int k,l;
    do{
        printf("MENU\n1.manage doctors\n2.manage patients\n3.appointment management\n4.test management\n5.billing system\n6.exit\n");
    printf("enter your choice:");
    scanf("%d",&k);
    switch(k){
        case 1:printf("1.add doctors\n2.view doctors\n");
               printf("enter your choice:");
               scanf("%d",&l);
               if(l==1){
                add_doctor();
                   
               }else if(l==2){
                view_doctor();
               }else{
                printf("enter the valid input!");
               }
               break;
        case 2:printf("1.add patients\n2.view patients\n");
               printf("enter your choice:");
               scanf("%d",&l);
               if(l==1){
                add_patient();
                   
               }else if(l==2){
                view_patient();
               }else{
                printf("enter the valid input!");
               }
               break;
        case 3:printf("1.schedule appointments\n2.view appointments\n");
               printf("enter your choice:");
               scanf("%d",&l);
               if(l==1){
                schedule_appointment();
                   
               }else if(l==2){
                view_appointments();
               }else{
                printf("enter the valid input!");
               }
               break;
        case 4:printf("1.view testss\n2.assign tests\n");
               printf("enter your choice:");
               scanf("%d",&l);
               if(l==1){
                view_tests();
                   
               }else if(l==2){
                  assign_tests();
               }else{
                printf("enter the valid input!");
               }
               break;
        case 5:
               generate_bill();
               break;
        
    }
    }while(k!=6);
    return 0; 
}
