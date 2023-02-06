#include <iostream>
#include <string>
#include <iomanip>
using namespace std;

struct mahasiswa
{
    int nim[20];
    string nama[50];
    string kelas[10];
    string prodi[20];
    string semester[20];
    string alamat[80];
};

int main()
{
    mahasiswa mhs;
    int a;
    int tmp, cari;
    int awal,akhir,tengah,ketemu=0;

    cout<<"===================================================================================="<<endl;
    cout<<"\n\t\tProgram Pendataan Mahasiswa Baru\n\t"<<endl;
    cout<<"===================================================================================="<<endl;
    cout<<"Masukkan Data Mahasiswa yang akan di input  : ";
    cin>>a;
    cout<<endl;

    for(int i=0; i<a; i++)
    {
        cout<<"Data mahasiswa ke  - "<<i+1 <<endl;
        cout<<"Masukkan Nim :";
        cin>> mhs.nim[i];
        cout<<"Nama  :";
        cin.ignore();
        getline(cin, mhs.nama[i]);
        cout<<"prodi  : ";
        getline(cin, mhs.prodi[i]);
        cout<<"kelas  : ";
        getline(cin, mhs.kelas[i]);
        cout<<"semester  : ";
        getline(cin, mhs.semester[i]);
        cout<<"Alamat    : ";
        getline(cin, mhs.alamat[i]);
        cout<<endl;
    }
    system("cls");
    cout<<endl;
    cout<<"\n\t\tPROGRAM PENDATAAN MAHASISWA BARU"<<endl;
    cout<<"===================================================================================="<<endl;
    cout<<"Nim\tNama\t\tkelas\t\tjurusan\t\tsemester\t\talamat"<<endl;
    cout<<"===================================================================================="<<endl;
    for(int k=0; k<a; k++){
	
        cout<<" "<<setiosflags(ios::left)<<setw(20)<<mhs.nim[k]<<" ";
        cout<<" "<<setiosflags(ios::left)<<setw(15)<<mhs.nama[k]<<" ";
        cout<<" "<<setiosflags(ios::left)<<setw(18)<<mhs.prodi[k]<<" ";
        cout<<" "<<setiosflags(ios::left)<<setw(14)<<mhs.kelas[k]<<" ";
        cout<<" "<<setiosflags(ios::left)<<setw(18)<<mhs.semester[k]<<" ";
        cout<<" "<<setiosflags(ios::left)<<setw(17)<<mhs.alamat[k]<<" ";
        cout<<endl;
    }
    cout<<"========================================================================================="<<endl;
    
    for(int b=0; b<a; b++){
        for (int j=b+1; j<a; j++){
            if (mhs.nim[b] > mhs.nim[j]){
                mhs.nama[b].swap (mhs.nama[j]);
                mhs.prodi[b].swap (mhs.prodi[j]);
                mhs.kelas[b].swap (mhs.kelas[j]);
                mhs.semester[b].swap (mhs.semester[j]);
                mhs.alamat[b].swap (mhs.alamat[j]);

                tmp=mhs.nim[b];
                mhs.nim[b]=mhs.nim[j];
                mhs.nim[j]=tmp;

            }
        }
    }
    cout<<endl;
    cout<<endl;
    cout<<"\n\t\tPROGRAM PENDATAAN MAHASISWA BARU"<<endl;
    cout<<"===================================================================================="<<endl;
    cout<<"Nim\tNama\t\tkelas\t\tjurusan\t\tsemester\t\talamat"<<endl;
    cout<<"===================================================================================="<<endl;
    cout<<" "<<endl;
    for(int k=0; k<a; k++){
        cout<<" "<<setiosflags(ios::left)<<setw(20)<<mhs.nim[k]<<" ";
        cout<<" "<<setiosflags(ios::left)<<setw(25)<<mhs.nama[k]<<" ";
        cout<<" "<<setiosflags(ios::left)<<setw(18)<<mhs.prodi[k]<<" ";
        cout<<" "<<setiosflags(ios::left)<<setw(14)<<mhs.kelas[k]<<" ";
        cout<<" "<<setiosflags(ios::left)<<setw(18)<<mhs.semester[k]<<" ";
        cout<<" "<<setiosflags(ios::left)<<setw(17)<<mhs.alamat[k]<<" ";
        cout<<endl;
    }
    cout<<"=========================================================================================="<<endl;
    
    cout<<endl;
    cout<<"CARI DATA ANDA DENGAN MENG-INPUT NIM ANDA : ";
    cin>>cari;
    awal = 0;
    akhir = a;
    while(ketemu == 0 && awal<=akhir){
        tengah = (awal+akhir)/2;
        if(mhs.nim[tengah] == cari){
            ketemu=1;
            break;
        }
        else if(mhs.nim[tengah] < cari){
            awal = tengah+1;
            break;
        }
        else{
            akhir= tengah-1;
        }
    }
    if(ketemu==1){
        cout<<"\n\nNim "<<cari<<" DItemukan di kolom tabel ke : "<<tengah+1<<endl;
    }
    else{
        cout<< "\n\nData anda tidak ditemukan!";
    }

    return 0;
}

