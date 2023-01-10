#include <iostream>
#include <chrono>
#include <thread>
using namespace std;
int size = 237;//171 for laptop, 237 for desktop
int main(int argc, char *argv[])
{
        int parent, mask, density;
        bool old_life[500] = {0}, new_life[500] = {0};
        srand(time(NULL));
        if (argc>1)
                if (argv[1][0] == 'r')
                        for (int x=0;x<size;x++)
                                old_life[x]=rand()%2;
        unsigned int rule = 0;
        if (argc>2)
                rule = atoi(argv[2]);
        old_life[size/2+1]=1;
        for (int y=0;y<10000;y++)
        {
                for (int x=0;x<size;x++)
                {
                        parent = 0;
                        if (x>0)
                                parent+=old_life[x-2]*1;//left parent is 2^0
                        parent+=old_life[x-1]*2;//center parent is 2^1
                        if (x<size)
                                parent+=old_life[x]*4;//right parent is 2^2
                        if (x>1)
                                parent+=old_life[x+1]*8;//left of left parent is 2^3
                        if (x<size-1)
                                parent+=old_life[x+2]*16;//right of right parent is 2^4
                        mask = 1 << parent;//Mask moves to the bit of its parent.
                        if (mask&rule)
                        {
                                new_life[x] = 1;
                                printf("\033[107m ");
                        }
                        else
                        {
                                new_life[x] = 0;
                                printf("\033[40m ");
                        }
                this_thread::sleep_for(100000ns);
                }
                cout << endl;
                swap(old_life, new_life);
        }
}
