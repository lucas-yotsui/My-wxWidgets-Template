# Projeto em C++ com wxWidgets para Interface Gráfica

## Introdução

Este repositório é um template para criação de projetos em C++ com interface gráfica para usuário utilizando a biblioteca wxWidgets. Por ser configurado como um template no Github, é possível cloná-lo sem copiar as informações de controle de versão deste. Dessa forma, seu projeto criado a partir de um clone deste template é tratado como novo e suas informações de controle de versão serão exclusivamente referentes a ele.

## Criando seu projeto

A melhor forma de criar seu novo projeto baseado neste template é através da interface do site Github ou da aplicação de linha de comando própria do Github, uma vez que o recurso de template é exclusivo deste. Para isso, siga as seguintes instruções: 
<style>
    ol {
        list-style: none;
        counter-reset: item;
    }

    li {
        counter-increment: item;
        margin-bottom: 5px;
    }

    li:before {
        margin-right: 10px;
        content: counter(item);
        background: lightblue;
        border-radius: 100%;
        color: black;
        width: 24px;
        height: 24px;
        text-align: center;
        display: inline-block;
    }

    li:after {
        content: " ";
        display: block;
        height: 10px
    }
</style>
<ol>
    <li>
        Entre na página do Github desse template.
        </li>
    <li>
        Clique no botão verde que diz <strong>Use this template</strong>.
    </li>
    <img src=https://imgur.com/T2eswUz.png style="margin: 0px 0px 20px"></img>
    <li>
        Clique na opção <strong>Create a new repository</strong>.
    </li>
    <li>
        Escolha um nome e opcionalmente uma descrição para seu novo projeto.
    </li>
    <img src=https://imgur.com/E4Ea0Ab.png style="margin: 0px 0px 20px"></img>
    <li>
        Escolha a visibilidade que deseja para o repositório do seu projeto.
    </li>
    <li>
        Clique em <strong>Create repository from template</strong>
    </li>
</ol>

_**Observação:** Pode ser usada a linha de comando convencional do Git, porém o repositório será clonado da forma padrão, incluindo todas as informações de versionamento e autoria do projeto. Nesse caso é necessário abrir a pasta onde foi clonado e deletar o diretório _.git_._

## Compilando

O projeto foi desenvolvido com o intuito de poder ser compilado em um ambiente Linux ou Windows, entretanto foi testado somente no Windows com MinGW, com Clang e GCC.

Conforme dito na introdução, o projeto foi desenvolvido utilizando CMake de tal forma que quando executado o comando para build, será instalado o wxWidgets automaticamente para compilação. Para isso, é clonado o repositório dessa biblioteca via Git e compilado, de forma a evitar a necessidade de possuir essa biblioteca instalada localmente. 

Essa decisão de projeto proporciona essa facilidade de automatizar o processo de obtenção da biblioteca e de sua ligação com o projeto, porém ao custo de tempos de compilação maiores.

O projeto foi desenvolvido tendo em mente o uso do editor **Visual Studio Code**, uma vez que sua extensão **Cmake Tools** facilita o uso de CMake para compilação, removendo a necessidade de uso de repetidos comandos via terminal. Além desta extensão, é recomendada também a extensão **C/C++ Extension Pack**, para usar colorização de destaque de sintaxe e outros recursos que facilitam o desenvolvimento em C/C++ _(Inclusive essa extensão já inclui a CMake Tools)_.

Utilizando o VS Code configurado desta forma, a compilação e execução do projeto é muito simples. Basta seguir o seguinte procedimento:
<ol>
    <li>
        Abrir a pasta do projeto no editor.
    </li>
    <li>
        Selecionar o kit de desenvolvimento usado pelo CMake.
    </li>
    <img src="https://imgur.com/f7UuZnn.png" style="margin: 0px 0px 20px"></img>
    <li>
        Aguardar a configuração inicial do CMake. Quando encerrada essa etapa, os recursos do wxWidgets já estão disponíveis para inclusão no código.
    </li>
    <li>
        Basta agora compilar seu projeto com o comando <strong>Build</strong>. Para isso, clique neste botão da barra de utilidades da extensão CMake Tools.
    </li>
    <img src="https://imgur.com/8pqi8D7.png" style="margin: 0px 0px 20px"></img>
    <li>
        Encerrada a compilação, basta executar seu programa. Para isso, clique neste botão da barra de utilidades da extensão CMake Tools.
    </li>
    <img src="https://imgur.com/c3KchnQ.png" style="margin: 0px 0px 20px"></img>
</ol>

Incluso neste projeto está um arquivo _main.cpp_ contendo um programa de exemplo da biblioteca, o qual deve criar a seguinte janela no evento de compilação e execução bem-sucedidas:
    <img src="https://imgur.com/c3KchnQ.png" style="margin: 10px 0px 20px"></img>

