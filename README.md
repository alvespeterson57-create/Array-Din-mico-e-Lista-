public class MeuArrayDinamico {
    private int[] dados;
    private int tamanho;

    public MeuArrayDinamico(int capacidadeInicial) {
        this.dados = new int[capacidadeInicial];
        this.tamanho = 0;
    }

    private void resize() {
        int[] novo = new int[dados.length * 2];
        for (int i = 0; i < dados.length; i++) {
            novo[i] = dados[i];
        }
        dados = novo;
    }

    public void add(int valor) {
        if (tamanho == dados.length) {
            resize();
        }
        dados[tamanho] = valor;
        tamanho++;
    }

    public int get(int indice) {
        if (indice < 0 || indice >= tamanho)
            throw new IndexOutOfBoundsException("Indice invalido: " + indice);
        return dados[indice];
    }

    public int size() {
        return tamanho;
    }

    public void imprimir() {
        StringBuilder sb = new StringBuilder("[");
        for (int i = 0; i < tamanho; i++) {
            sb.append(dados[i]);
            if (i < tamanho - 1) sb.append(", ");
        }
        sb.append("]");
        System.out.println(sb.toString());
    }
}
