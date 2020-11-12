
~/.vimrc
```bash
colorscheme industry
set nu       "mostra numeração de linhas
set showmode "mostra o modo em que estamos
set showcmd  "mostra no status os comandos inseridos
set ts=4     "tamanho das tabulações
set ts=2     "tamanho das tabulações = set tabstop=2
filetype plugin indent on "Interpretacao do tipo de arquivo
syntax on    "habilita cores
set hls      "destaca com cores os termos procurados
set incsearch "habilita a busca incremental
set ai       "auto identação
set ignorecase "faz o vim ignorar maiúsculas e minúsculas nas buscas
set smartcase  "Se começar uma busca em maiúsculo ele habilita o case
set cul        "abreviação de cursor line (destaca linha atual)
set ve=all     "permite mover o cursor para áreas onde não há texto
set ttyfast    "Envia mais caracteres ao terminal, melhorando o redraw de janelas. 
set shiftwidth=2 "Deixa coerente com o tab ao dar enter
set backspace=2 "Habilita a exclusãod e caracteres ao usar backspace
set fileencoding=iso-8859-1 " Define a codificação para salvar
set encoding=iso-8859-1 " Define a codificação para a abertura de arquivos
set expandtab " Usar espaços no lugar de tabs
set softtabstop=2 " Backspace deve respeitar a identação

```


- **Row navigation**  
(k) Down  
(j) Up  
(h) Right  
(l) Left  

Examples:  
10 + k 

## Commands
- New line + insert mode : (o)
- New line up + insert mode : (shift + o)
- Copy : (y)
- Paste : (p)
- Begin of file: (gg)
- End of file (shift + g)
- Indent line (==)
- Replace (r + character)

## Modes
- **Insert** (i)
- **Visual** (v)
- **Visual Line** (shift + v)
- **Visual Block** (ctrl + v)

## Splitt screen
- Vertical :  vs <path_file>
- Horizontal: sp <path_file>
- Navegation: ctrl + ww
- Zoom: ctrl+w + _
- Zoom restart: ctrl+w + 0

## Plugins
- NERDTree 
  - (s) Select a new file and split the screen

## Insert new colorscheme
- Download the file of the scheme in ~/.vim/colors
- Set parameter colorscheme in .vimrc

## Record a sequence of commands

(q) + some key (ex.: q + a)
insert the commands
(q)
To execute de sequence of commands, press @ + key (Ex.: @ + a)
