#include <stdio.h>

int n, target;
int arr[20];
int subset[20];

int solutions[1 << 20][20];
int solutionSize[1 << 20];
int solutionCount = 0;

void findSubsets(int index, int currentSum, int size)
{
    if (index == n)
    {
        if (currentSum == target)
        {
            for (int i = 0; i < size; i++)
                solutions[solutionCount][i] = subset[i];

            solutionSize[solutionCount] = size;
            solutionCount++;
        }
        return;
    }

    // Include current element
    subset[size] = arr[index];
    findSubsets(index + 1, currentSum + arr[index], size + 1);

    // Exclude current element
    findSubsets(index + 1, currentSum, size);
}

int main()
{
    scanf("%d", &n);

    for (int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    scanf("%d", &target);

    findSubsets(0, 0, 0);

    if (solutionCount == 0)
    {
        printf("-1\n");
    }
    else
    {
        // Print in reverse order of discovery
        for (int i = solutionCount - 1; i >= 0; i--)
        {
            for (int j = 0; j < solutionSize[i]; j++)
            {
                printf("%d ", solutions[i][j]);
            }
            printf("\n");
        }
    }

    return 0;
}
