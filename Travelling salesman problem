#include <stdio.h>
#include <limits.h>

#define MAX 20
#define INF 1000000000

int n;
int cost[MAX][MAX];
int dp[1 << MAX][MAX];

int tsp(int mask, int pos)
{
    // All cities visited: return to starting city
    if (mask == (1 << n) - 1)
    {
        if (cost[pos][0] == -1)
            return INF;

        return cost[pos][0];
    }

    // Already calculated
    if (dp[mask][pos] != -1)
        return dp[mask][pos];

    int ans = INF;

    for (int city = 0; city < n; city++)
    {
        // City not visited and edge exists
        if (!(mask & (1 << city)) && cost[pos][city] != -1)
        {
            int newCost = cost[pos][city] +
                          tsp(mask | (1 << city), city);

            if (newCost < ans)
                ans = newCost;
        }
    }

    return dp[mask][pos] = ans;
}

int main()
{
    scanf("%d", &n);

    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            scanf("%d", &cost[i][j]);
        }
    }

    // Initialize DP table
    int totalStates = 1 << n;

    for (int i = 0; i < totalStates; i++)
    {
        for (int j = 0; j < n; j++)
        {
            dp[i][j] = -1;
        }
    }

    // Start from city 0
    int answer = tsp(1, 0);

    if (answer == INF)
        printf("-1\n");
    else
        printf("%d\n", answer);

    return 0;
}
