
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
```


- **Row navigation**  
(k) Down  
(j) Up  
(h) Right  
(l) Left  

Examples:  
10 + k 

## Modes
- **Visual** (v)
- **Visual Line** (shift + v)
- **Visual Block** (ctrl + v)

