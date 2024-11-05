### Angular CLI ###
#### Instalação 
```npm install -g @angular/cli@<version>```
#### Novo projeto 
```ng new <new-project>```

#### Sintaxe básica de módulo

```javascript
import { NgModule } from '@angular/core';
import { PessoaComponent } from './pessoa.component.ts';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from "@angular/forms";

@NgModule({
  declarations: [PessoaComponent] // Componentes do módulo
  imports: [BrowserModule, FormsModule] // Copmonentes externos
  providers: [], // Serviços que estarão no escobo global do módulo
  bootstrap: ['PessoaComponent'] // Componente de inicialização
})
export class AppModule {}
```

#### Sintaxe básica de componente

```javascript
import { Component } from '@angular/core';
@Component({
  selector: 'pessoa-pessoa',
  templateUrl: './pessoa.component.ts',
  styleUrls: ['./pessoa.component.css'],
  standalone: false // Versão > angular 14
})
export class PessoaComponent {}

/* Inclusão do seletor no arquivo .hmtl do componente pai */
<app-pessoa></app-pessoa>
```

#### Passagem de parâmetros do Componente Pai para o filho
```javascript
import { Input } from '@angular/core';
{...}
export class PessoaComponent {
  @Input() nomePessoa: string = '';
}
/* Utilização do componente */
<app-pessoa [nomePessoa]="variavelNoComponentePai" />
```

#### Chamada de um método do componente pai no componente filho
```javascript
/* Componente filho */
import { Output, EventEmitter } from '@angular/core';
{...}
export class PessoaComponent {
  @Output() atualizarNome = new EventEmitter<string>;

  onUpdateName() {
    this.atualizarNome.emmit('Marcelo')
  }
}

/* Componente pai */
{...}
export class AppComponent {
  novoNome = '';
  onAtualizarNome(nome: string) {
    novoNome = nome;
  }
}

/* Utilização do componente no pai*/
<app-pessoa (atualizarNome)="onAtualizarNome($event)" />
```
#### Databinding
```javascript
/* One way databinding */
<app-pessoa [value]="variavelComValor" (click)="umaFuncao" />
/* Two way data binding
<app-pessoa [(ngModel)]="personName"
```

#### Routing
```javascript
/* Adicionar o arquivo app-routing.module.ts */
import { NgModule } from "@angular/core";
import { RouterModule, Routes } from "@angular/router";
import { ListaComponent } from './lista.component.ts';
import { FormComponent } from './form.component.ts';

const routes: Routes = [
  {path: '', component: ListaComponent },
  {path: 'form', component: FormComponent },

]
@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}

/* Este módulo deve ser importado no Modulo principal da aplicação */
    {...}
    imports: [BrowserModule, FormsModule, AppRoutingModule],
    providers:[],
    bootstrap: [AppComponent]
})
export class AppModule {}
```


