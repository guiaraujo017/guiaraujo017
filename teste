graph LR

    subgraph "1. Inicio do Cadastro" TD
        A[Inicio: Pre-cadastro de Candidatos] --> B(Diretorio Estadual Confecciona Lista)
        B --> C[Diretorio Estadual Alimenta Dados no Sistema PL]
        C --> D[Sistema PL Emite Anexo II]
        D --> E{Anexo II Assinado Digitalmente Gov.br?}
        E -- Sim --> F[Anexo II Gravado no Sistema PL]
        E -- Nao --> G[Corrigir Assinatura Anexo II]
        G --> E
    end

    subgraph "2. Sincronizacao e Acesso" TD
        H[Sistema PL Sincroniza com TSE] --> I[Sistema PL Envia Link de Acesso ao Candidato]
        I --> J{Candidato Recebe Link?}
        J -- Nao --> K[Contato com Diretorio Estadual/Ordenador para Conferencia]
        K --> I
        J -- Sim --> L[Candidato Acessa Sistema PL e Preenche Dados]
    end

    subgraph "3. Preenchimento e Validacao pelo Candidato" TD
        M{Dados Bancarios Preenchidos?}
        L -- Sim --> M
        M -- Nao --> N[Preencher Dados Bancarios]
        N --> M
        M -- Sim --> O{Dados Incorretos no Sistema PL?}
        O -- Sim --> P[Candidato Corrige Dados no TSE - Genero Cor Raca]
        P --> L
        O -- Nao --> Q[Candidato Le e Aceita Termos e LGPD]
        Q --> R[Sistema PL Confecciona Anexo I - Requerimento FEFC]
        R --> S{Anexo I Assinado Digitalmente Gov.br?}
        S -- Sim --> T[Anexo I Gravado no Sistema PL]
        S -- Nao --> U[Corrigir Assinatura Anexo I]
        U --> S
        T --> V[Candidato Insere Contrato de Abertura de Contas Bancarias]
        V --> W[Dossie do Candidato Composto - Anexo I e Contrato]
    end

    subgraph "4. Conferencia e Aprovacao Final" TD
        X[Conferencia de Status e Dados do Candidato]
        W --> X
        X --> Y{Divergencia Encontrada?}
        Y -- Sim --> Z[Transacao Negada, Erro Indicado para Correcao]
        Z --> X
        Y -- Nao --> AA[Geracao de Lista para Apreciacao por lotes]
        AA --> BB[Apreciacao do Presidente do Diretorio Nacional]
        BB --> CC{Decisao do Presidente?}
        CC -- Excluir Candidato --> DD[Transacao Suspensa]
        CC -- Corrigir Valor --> EE[Correcao pelo Operador Financeiro]
        EE --> FF[Transacao Segue para Pagamento]
    end

    subgraph "5. Pagamento" TD
        GG[Lote Direcionado para Execucao do Pagamento]
        FF --> GG
        GG --> HH[Pagamento Via Chave PIX - API Banco do Brasil]
        HH --> II[Geracao de Arquivo de Retorno]
        II --> JJ{Recebimento da Verba Positivo?}
        JJ -- Sim --> KK[Transacao Finalizada]
        JJ -- Nao --> LL[Retorno ao Diretorio Estadual/Ordenador - Status Motivado]
    end

    %% Conectando os subgrafos horizontalmente e fluxos de retorno
    F --> H
    LL --> X
    KK --> FIM((FIM))
    DD --> FIM
