# Tradutor Português-Inglês baseado em Transformer

Este projeto implementa um sistema de tradução automática neural usando a arquitetura Transformer para traduzir entre português e inglês.

## Análise de Desempenho

### Experiência de Treinamento
- **Treinamento em CPU**: Tentativas de treinamento em CPU foram extremamente demoradas
  - Não completou o treinamento total
  - Várias horas de processamento com progresso limitado
  - Não prático para desenvolvimento completo do modelo

- **Treinamento em GPU (T4)**:
  - Completou o treinamento em aproximadamente 30 minutos
  - Aceleração significativa comparada à CPU
  - Tornou o processo de desenvolvimento muito mais viável

### Vantagens da Arquitetura Transformer
1. **Processamento Paralelo**
   - Processa sequências inteiras simultaneamente
   - Muito mais rápido que o processamento sequencial RNN

2. **Mecanismo de Atenção**
   - Melhor tratamento de dependências de longo alcance
   - Captura contexto mais efetivamente que modelos seq2seq tradicionais

3. **Qualidade das Traduções**
   - Lida bem com estruturas complexas de frases
   - Mantém contexto em frases mais longas
   - Boa preservação do significado entre idiomas

4. **Visualização**
   - Pesos de atenção podem ser visualizados
   - Ajuda a entender a tomada de decisão do modelo
   - Útil para depuração e melhorias

### Limitações e Desafios
1. **Requisitos de Recursos**
   - Requer poder computacional significativo
   - Aceleração GPU fortemente recomendada
   - Alto uso de memória durante o treinamento

2. **Dependências de Dados de Treinamento**
   - Requer grande corpus paralelo
   - Qualidade muito dependente dos dados de treinamento
   - Pode ter dificuldades com palavras/frases raras

3. **Peculiaridades na Tradução**
   - Às vezes produz traduções muito literais
   - Pode ter dificuldades com expressões idiomáticas
   - Pode ter dificuldade com conteúdo muito técnico

4. **Épocas de Treinamento Limitadas**
   - Modelo atual treinado por apenas 20 épocas
   - Mostra sinais de alucinação nas traduções
   - Mais épocas de treinamento necessárias para maior estabilidade

### Resultados dos Testes
Os testes finais mostraram resultados variados com diferentes tipos de frases, demonstrando tanto as capacidades quanto as limitações do modelo:

1. Expressões básicas (mostrando problemas de alucinação):
   ```
   Entrada: "O cachorro late e o pintinho pia."
   Saída: "the dog is the paintbrush."
   ```

2. Comparação direta Inglês-Português:
   ```
   Entrada: "Hi, i am writing in english to test this translator."
   Saída: "hym, immod innospeare transor."
   
   Entrada: "Olá, estou escrevendo em ingles para testar este tradutor."
   Saída: "hi, i'm writing in english to test this translator."
   ```

3. Expressões coloquiais (tratamento inadequado):
   ```
   Entrada: "Olha que coisa mais legal"
   Saída: "look at that more legally than ever - legally."
   ```

4. Frases simples com erros de contexto:
   ```
   Entrada: "Quero comprar uma barraca nova para acampar"
   Saída: "i want to buy a new bargain to chapate."
   ```

5. Frases complexas com problemas de vocabulário:
   ```
   Entrada: "Vou ao shopping comprar camisas para ir ao trabalho"
   Saída: "i'm going to buy ripple to go work."
   ```

6. Estruturas de perguntas:
   ```
   Entrada: "Que música é essa?"
   Saída: "what does that music look like?"
   ```

Estes resultados de teste demonstram claramente que, embora o modelo possa lidar com algumas traduções básicas, ainda apresenta problemas significativos com:
- Alucinações (gerando conteúdo não relacionado)
- Má interpretação de contexto
- Tratamento inadequado de expressões coloquiais
- Escolhas incorretas de vocabulário
- Traduções literais que não preservam o significado

## Conclusão
O tradutor baseado em Transformer demonstra forte potencial para tradução Português-Inglês, especialmente quando treinado adequadamente com aceleração GPU. Embora o modelo mostre capacidades impressionantes com construções linguísticas padrão, há espaço para melhorias no tratamento de expressões coloquiais e vocabulário especializado.

### Melhorias Futuras
- Expandir conjunto de dados de treinamento com conteúdo mais diversificado
- Ajustar hiperparâmetros para melhor desempenho
- Implementar treinamento específico por domínio para traduções especializadas
- Otimizar tamanho do modelo para melhor eficiência de recursos