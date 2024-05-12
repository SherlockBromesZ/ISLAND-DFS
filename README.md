# ISLAND-DFS

'''cpp
#include<bits/stdc++.h>
using namespace std;

// Função DFS para explorar e marcar as células da grade.
void dfs(int x, int y, vector<vector<int>>& grid, vector<vector<bool>>& visited) {
    int n = grid.size(); // Número de linhas na grade.
    int m = grid[0].size(); // Número de colunas na grade.
    
    // Verifica se a posição atual é válida, não visitada e é terra.
    if (x < 0 || x >= n || y < 0 || y >= m || visited[x][y] || grid[x][y] == 0) return;
    
    // Marca a célula atual como visitada.
    visited[x][y] = true;
    
    // Chama a função DFS nas quatro direções adjacentes.
    dfs(x + 1, y, grid, visited);
    dfs(x - 1, y, grid, visited);
    dfs(x, y + 1, grid, visited);
    dfs(x, y - 1, grid, visited);
}

// Função para contar o número de ilhas na grade.
int countIslands(vector<vector<int>>& grid) {
    int n = grid.size(); // Número de linhas na grade.
    int m = grid[0].size(); // Número de colunas na grade.
    vector<vector<bool>> visited(n, vector<bool>(m, false)); // Grade para manter o controle das células visitadas.
    int count = 0; // Contador de ilhas.
    
    // Percorre todas as células da grade.
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            // Se a célula não foi visitada e é terra, realiza uma busca em profundidade.
            if (!visited[i][j] && grid[i][j] == 1) {
                dfs(i, j, grid, visited);
                count++; // Incrementa o contador de ilhas.
            }
        }
    }
    return count; // Retorna o número total de ilhas.
}

// Função principal para executar o programa.
int main() {
    vector<vector<int>> grid = {
        {1, 1, 0, 0, 0},
        {1, 1, 0, 0, 0},
        {0, 0, 1, 0, 0},
        {0, 0, 0, 1, 1}
    };
    cout << countIslands(grid) << endl; // Saída: 3
    return 0;
}
'''
