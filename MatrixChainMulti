
void Print_2d(vector<vector<int>> arr, int n){
    for(int i=0; i<n; i++){
        for(int j=0; j<n; j++){
            cout<<arr[i][j]<<"   ";
        }
        cout<<endl;
    }
}

void Cost(int arr[], int n){
    string names="";
    for(int ch=65; ch<65+n-1; ch++){
        names+=(char)ch;
//        cout<<ch<<endl;
    }
    n--;
    int dp[n][n];
    vector<vector<string>> eqn(n,vector<string>(n));
    
    for(int i=0; i<n; i++){
        for(int j=0; j<n; j++){
            eqn[i][j]=" ";
            if(j<i)
                dp[i][j]=-1;
            else
                dp[i][j]=0;
        }
    }
    for(int g=0; g<n; g++){
        for(int i=0, j=g; j<n; i++, j++){
            if(g==0){
                dp[i][j]=0;
                eqn[i][j]=names[i];
                continue;
            }
            if(g==1){
                dp[i][j]=(arr[i]*arr[i+1]*arr[i+2]);
                eqn[i][j]="(";
                eqn[i][j]+=names[i];
                eqn[i][j]+=names[j];
                eqn[i][j]+=")";
                continue;
            }
            int val1=0, val2=0;
            val1=dp[i][i]+dp[i+1][j]+(arr[0]*arr[1]*arr[j+1]);  // A(BC)
            val2=dp[i][j-1]+(arr[0]*arr[j]*arr[j+1]);           // (AB)C
            dp[i][j]=min(val1, val2);
        }
    }
    cout<<endl;
    Print_2d((int*)dp, n);
    cout<<endl<<endl;
    
    for(int g=2; g<n; g++){
        for(int i=0, j=g; j<n; i++, j++){
            if(dp[i][j-1]<dp[i+1][j]){
                eqn[i][j]+="(";
                eqn[i][j]+=eqn[i][j-1];
                eqn[i][j]+=names[j];
                eqn[i][j]+=")";
            }
            else{
                eqn[i][j]+="(";
                eqn[i][j]+=names[i];
                eqn[i][j]+=eqn[i+1][j];
                eqn[i][j]+=")";
            }
        }
    }
    Print_2d(eqn, n);
    cout<<endl<<eqn[0][n-1]<<endl;
}

int main(){
    int arr[]={10,20,30,40,50,60};
    Cost(arr, 6);
}
