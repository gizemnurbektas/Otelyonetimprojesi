#include <stdio.h>
//Çağırıldığında sırasıyla tüm boş ve dolu odaları ekrana bastırır
void dbgoster(char odalar[]){
    printf("\n\n*************************\n\n");
    printf("Bos odalar:\n");

    for(int i=0;i<5;i++){
        if(odalar[i]=='b'){
            printf("%d. ",i+1);
        }    
    }

    printf("\nDolu odalar:\n");

    for(int i=0;i<5;i++){
        if(odalar[i]=='d'){
            printf("%d. ",i+1);
        }    
    }
    printf("\n*************************\n");
}
//alınan diziden ve parametreden istenilen odanın degerini d yapar(doldur)
void doldur(char odalar[],int x){
     odalar[x-1]='d';
}
//alınan diziden ve parametreden istenilen odanın degerini b yapar(bosaltır)
void bosalt(char odalar[],int x){
     odalar[x-1]='b';
}
//Sadece printf fonksiyonlarını kullanır mainin içini temiz göstermek için oluşturulmuş bir fonksiyon
void menugoster(){
    printf("\nOdalarin musaitlik durumunu ogrenmek icin A'ya:\n");
    printf("Odanin kaç kisilik oldugunu ogrenmek icin B'ye:\n");
    printf("Oda fiyatini ogrenmek icin C'ye:\n");
    printf("Odayi doldurmak icin D'ye:\n");
    printf("Odayi bosaltmak icin E'ye:\n");
}
//gönderilen diziyi sırasıyla bastırarak içini gösterir(odada kalabilecek kişi sayısını gösterir)
void odakisigoster(int odakisi[]){
    for(int i=0;i<5;i++){
        printf("%d. oda %d kisilik\n",i+1,odakisi[i]);
    }
}
//gönderilen diziyi sırasıyla bastırarak içini gösterir(odanın fiyatını gösterir)
void odafiyatgoster(int odafiyat[]){
    printf("Oda fiyatlari:\n");
    for(int i=0;i<5;i++){
        printf("%d. oda : %d tl\n",i+1,odafiyat[i]);
    }
}


int main()
{
    //her dizi indeksi bir odayı gösterir farklı diziler farklı özelliklere tekabul eder
	char odalar[5]={'b','b','b','b','b'};
	int odakisi[5]={1,2,2,3,4}; 
	int odafiyat[5]={100,200,200,300,400};

    printf("Otel Yonetim Programina Hosgeldiniz....\n\n\n\n");
    
    char secim;
    char devam='y';
    //tek bir işlemde bitmemesi için sonsuz döngüye alınır
    while(1){
        menugoster();
        printf("Yapmak istediginiz islemi secin:");
        
        scanf(" %c",&secim);
        if(secim=='A' || secim=='a'){
            dbgoster(odalar);    
        }
        else if(secim=='B' || secim=='b'){
            odakisigoster(odakisi);
        }
        else if(secim=='C' || secim=='c'){
            odafiyatgoster(odafiyat);    
        }
        else if(secim=='D' || secim=='d'){
            int x;
            printf("Doldurmak istediginiz odayi secin:");
            scanf("%d",&x);
            if(x<6 && x>0){
                doldur(odalar,x);    
            }
            else{
                printf("Oyle bir oda yok!!!!!!!\n");
            }
        }
        else if(secim=='E' || secim=='e'){
            int x;
            printf("Bosaltmak istediginiz odayi secin:");
            scanf("%d",&x);
            if(x<6 && x>0){
                bosalt(odalar,x);    
            }
            else{
                printf("Oyle bir oda yok!!!!!!!\n");
            }    
        }
        else{
            printf("Gecersiz bir islem istediniz....\n");
            return 0;
        }
        printf("\nDevama etmek icin y 'ye basiniz:");
        scanf(" %c",&devam);
        if(devam=='y'||devam=='Y'){
            continue;
        }
        else{
            printf("Program Sona erdi....");
            break;
        }
    }
    
    
    return 0;
}
