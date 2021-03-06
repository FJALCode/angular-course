# Curso Base de Angular

* [Proyecto de Angular](#proyecto-de-angular)
* [Combados básicos](#combados-básicos)
* [Estructura de un proyecto de Angular](#estructura-de-un-proyecto-de-angular)
* [Componentes](#componentes)
  * [ngOnChanges](#ngonchanges)
  * [ngOnInit](#ngoninit)
  * [ngDoCheck](#ngdocheck)
  * [ngAfterContentInit](#ngaftercontentinit)
  * [ngAfterContentChecked](#ngaftercontentchecked)
  * [ngAfterViewInit](#ngafterviewinit)
  * [ngAfterViewChecked](#ngafterviewchecked)
  * [ngOnDestroy](#ngondestroy)
* [Servicios](#servicios)
* [Directivas](#directivas)
* [Módulo](#módulo)
* [CommonModule](#commonmodule)
  * [ngIf](#ngif)
  * [ngFor](#ngfor)
  * [ngStyle](#ngstyle)
  * [ngClass](#ngclass)
  * [ngSwitch](#ngSwitch)
* [Navegación en Angular](#navegación-en-angular)
  * [Routes File](#routes-file)
  * [RouterModule.forRoot vs RouterModule.forChild](#routermoduleforroot-vs-routermoduleforchild)
  * [Lazy Loading](#lazy-loading)
  * [RouterLink y RouterLinkActive](#routerlink-y-routerlinkactive)
  * [Router](#router)
  * [ActivatedRoute](#activatedroute)  
  * [Rutas Anidadas](#rutas-anidadas)  
* [Decoradores](#decoradores)
  * [@Input](#input)
  * [@Output](#output)
* [Guard](#guard)
* [Pipes](#pipes)
  * [Uppercase](#uppercase)
  * [Lowercase](#lowercase)
  * [Slice](#slice)
  * [Decimal](#decimal)
  * [Percent](#percent)
  * [Currency](#currency)
  * [Json](#json)
  * [Async](#async)
  * [Date](#date)  
  * [Personalizado](#personalizado)  
  * [DomSeguro](#domseguro)  
* [Peticiones HTTP](#peticiones-http)
  * [Get](#Get)
  * [Post](#Post)
  * [Put](#Put)
  * [Delete](#Delete)
* [RxJS](#rxjs)
  * [Partes del RxJS](#partes-del-rxjs)
  * [Patrón Iterador](#patrón-iterador)
    * [hasNext() & next()](hasnext-next)
  * [Operadores RxJS](#operadores-rxjs) 
    * [of()](#of)
    * [from()](#from)
    * [Pipe()](#pipe)
    * [Map()](#map)  
  * [Suscribe()](#suscribe)   
  * [Subjects](#subjects)
  * [Operadores RxJs vs Función de Orden Superior](#operadores-rxjs-vs-función-de-orden-superior)
* [Storage](#storage)
  * [Local Storage](#local-storage)
  * [Session Storage](#session-storage)
* [Template Forms](#template-forms)
* [Reactive Forms](#reactive-forms)
  * [FormControl](#formcontrol)
  * [FormGroup](#formgroup)
      * [FormGroup.get()](#formgroupget)
      * [FormGroup.setValue()](#formgroupsetvalue)
      * [FormGroup.reset()](#formgroupreset)
      * [FormGroup.valueChanges](#formgroupvaluechanges)
      * [FormGroup.statusChanges](#formgroupstatuschanges)
  * [FormBuilder](#formbuilder)
  * [Nested Forms](#nested-forms)
  * [FormArray](#formrray)
      * [FormArray.push()](#formarraypush)
      * [FormArray.removeAt()](#formarrayremoveat)
  * [Validators](#validators)
    * [Validaciones sincrónicas](#validaciones-sincrónicas)
    * [Validaciones asíncronas](#validaciones-asíncronas)   
* [Bootstrap](#bootstrap)
* [Angular Material](#angular-material)
  * [Instalación y Configuración](#instalación-y-configuración)
  * [MatButton](#matbutton)
  * [MatCard](#matcard)


 
## Proyecto de Angular
Angular es un lenguaje basado en `componentes`, por lo general una app de angular se basa en múltiples componentes, como pudiesen ser el menú de navegación, barra lateral, páginas y subpáginas, pie de páginas, etc.

<img src="img/componentes_angular.png" width="auto;"/>

Las `directivas estructurales` son instrucciones que le indicarán a la sección de HTML que hacer, por ejemplo `*ngIf`, `*ngFor`
<img src="img/directivas_estructurales.png" width="auto;"/>

## Combados básicos
*   **`ng new app-name`:** Permite la creación de un nuevo proyecto de Angular bajo el nombre `app-name` y parámetros indicados
*   **`ng serve`:** Permite instanciar el proyecto de angular en el puerto establecido por defecto levanta en el `4200`. 
    * Usamos la bandera **`-p`** para indicar el puerto donde deseamos que abra `ng serve -p 4201`.
    * Usamos la bandera **`-o`** para indicar que una vez que cargue, abra el navegador por defecto `ng serve -o`.
*   **`ng generate component ruta`:** Crea un nuevo componente en nuestro proyecto de angular en la ruta indicada, por default lo cera en la carpeta `app`, podemos abreviar la petición `ng g c components/footer`, Este comando creará el componente en la ruta `src/app/components/footer/footer.component.ts`.
    * Usamos la bandera **`-s`**`(--inline-style)` para generar componentes sin el archivo de estilos.
    * Usamos la bandera **`-t`**`(--inline-template)` para generar componentes sin la plantilla HTML en el component.ts.
    * Usamos la bandera **`--skip-tests`** para generar componentes sin el archivo `.spec`.
    * Usamos la bandera **`--flat`** para generar componentes en la ruta principal o en una especifica sin crear una carpeta que haga alusión al nombre del mismo.
*   **`ng generate service ruta`:** Crea un servicio en la ruta indicada, por default lo crea en la carpeta `app`, podemos abreviar la petición `ng g s services/spotify`, Este comando creará el servicio en la ruta `src/app/services/spotify.service.ts`.
    * Usamos la bandera **`--skip-tests`** para generar el servicio sin el archivo `.spec`.
    * Usamos la bandera **`--flat`** para generar componentes en la ruta principal o en una especifica sin crear una carpeta que haga alusión al nombre del mismo.
*   **`ng generate directive ruta`:** Crea una directiva personalizada en la ruta indicada, por default lo crea en la carpeta `app`, podemos abreviar la petición `ng g d directives/resaltado`, Este comando creará la directiva en la ruta `src/app/directives/resaltado/resaltado.directive.ts`.
    * Usamos la bandera **`--skip-tests`** para generar la directiva sin el archivo `.spec`.
    * Usamos la bandera **`--flat`** para generar componentes en la ruta principal o en una especifica sin crear una carpeta que haga alusión al nombre del mismo.
*   **`ng generate pipe ruta`:** Crea un pipe personalizado en la ruta indicada, por default lo crea en la carpeta `app`, podemos abreviar la petición `ng g p pipes/capitalizado`, Este comando creará el pipe en la ruta `src/app/pipes/capitalizado/capitalizado.pipe.ts`.
    * Usamos la bandera **`--flat`** para generar componentes en la ruta principal o en una especifica sin crear una carpeta que haga alusión al nombre del mismo.
*   **`ng generate guard ruta`:** Crea un guard en la ruta indicada, por default lo crea en la carpeta `app`, podemos abreviar la petición `ng g guard guards/auth`, Este comando creará la directiva en la ruta `src/app/guards/guard/auth.guard.ts`.
    * Usamos la bandera **`--skip-tests`** para generar el guard sin el archivo `.spec`.
    * Usamos la bandera **`--flat`** para generar componentes en la ruta principal o en una especifica sin crear una carpeta que haga alusión al nombre del mismo.


## Estructura de un proyecto de Angular
```sh
├── e2e                    //Carpeta destinada a la realización de pruebas unitarias y de integración.
├── node_modules           //Carpeta destinada a los módulos de node.
├── src                    //Carpeta donde se guardara el source code del api
│   ├── app                //Carpeta estandar con la primera APP de angular.
│   │   ├── components     //Carpeta que contendrá los componentes a crear.
│   │   ├── directives     //Carpeta que contendrá las directivas a crear.
│   │   ├── guards         //Carpeta que contendrá los guards a crear.
│   │   ├── pipes          //Carpeta que contendrá los pipes a crear.
│   │   ├── services       //Carpeta que contendrá los servicios a crear.
│   │   ├── app.component.css      //Archivo de estilos del componente app.
│   │   ├── app.component.html     //Archivo html del componente app.
│   │   ├── app.component.spec.ts  //Archivo de pruebas automáticas del componente app
│   │   ├── app.component.ts       //Archivo de typescript del componente app
│   │   ├── app.module.ts          //Archivo de módulos del componente app
│   ├── assets             //Carpeta que contiene recursos estáticos (imágenes/librerías externas). 
│   │   ├── .gitkeep       //Archivo para mantener la carpeta al subir a un repositorio.
│   ├── environments       //Carpeta que contiene los ambientes de la APP. 
│   │   ├── environment.prod.ts    //Archivo con ambiente de producción.
│   │   ├── environment.ts         //Archivo con ambiente de desarrollo.
│   ├── favicon.ico        //Icono que representa la página en las pestañas.
│   ├── index.html         //Página web inicial que renderizar
│   ├── main.ts            //Archivo con el primer código a usar para lanzar la APP
│   ├── polyfills.ts       //Archivo que ayuda a la compatibilidad entre versiones viejas de navegadores
│   ├── styles.css         //Archivo para manejar los estilos globales de la APP
│   └── test.ts            //Archivo que contiene todas las rutas de los servicios desarrollados.
├── karma.conf.js          //Archivo de configuración de las pruebas de Karma.
├── .editconfig            //Archivo de configuraciones propías del editor.
├── .gitignore             //Archivo que permitirá que el repositorio de git ignore todos los archivos detallados en él
├── angular.json           //Archivo que permite indicarle a Angular el funcionamiento de la APP.
├── package.json           //Archivo donde se ven los paquetes o dependencias instaladas en el proyecto.
├── package-lock.json      //Archivo que deja un rastro de como fue creado el package.json
├── tsconfig.json          //Archivo que indicar los estándares de typescript a usar
├── tslint.json            //Archivo que vigila como escribimos nuestro código, en base a las reglas que especificamos
├── tsconfig.app.json      //Archivo con configuraciones propias de typescript para la APP
├── tsconfig.spec.json     //Archivo con configuraciones propias para las pruebas de  typescript en la APP
└── README.md              //Información general del proyecto
```

## Componentes
Los `componentes` son clases con bloques de código re-utilizable que poseen un decorador específico y ejecután una acción en particular, consta básicamente de:
* **`Component.css`**: Archivo de estilos del componente app.
* **`Component.html`**: Archivo html del componente app.
* **`Component.spec.ts`**: Archivo de pruebas automáticas del componente app
* **`Component.ts`**: Archivo de typescript del componente app, incluirá:
  *   **`@Component`:** Decorador base de Angular que proporcionará datos de configuración a fin de indicar como procesar, instanciar y usar el componente en tiempo de ejecución.
  *   **`selector`:** Le indicará a Angular que cuando sea escogido deberá renderizar el `templateUrl`
  *   **`templateUrl`:** Ruta donde se encontrará la plantilla a renderizar
  *   **`styleUrls`:** Ruta del archivo estilo a aplicar (CSS, SASS, etc), unicamente al componente creado 

  ```ts
  import { Component } from '@angular/core';

  @Component({
    selector: 'app-header',
    templateUrl: './header.component.html',
    styleUrls: ['./header.component.css']
  })
  export class HeaderComponent {
  }
  ```

Para indicarle a angular que el componente creado es uno el cual puede utilizar basta con dirigirse al `app.module.ts`, importar la ruta del nuevo componente creado y declararlo en la sección `declarations`

```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';
import { HeaderComponent } from './components/header/header.component'

@NgModule({
  declarations: [
    AppComponent,
    HeaderComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

El ciclo de vida de un componente o `lifecycle hook` esta compuesto por 8 etapas denominadas `lifecycle hook event` o `evento de enlace de ciclo de vida`

<img src="img/ciclo_vida.png" width="auto;"/>


#### ngOnChanges
Este evento se ejecuta cada vez que se cambia un valor de un input control dentro de un componente. Se activa primero cuando se cambia el valor de una propiedad vinculada. Siempre recibe un change data map o mapa de datos de cambio, que contiene el valor actual y anterior de la propiedad vinculada envuelta en un SimpleChange
```ts
import { Component, OnChanges } from '@angular/core';

@Component({
  selector: 'app-home',
  template: `
    <app-ng-style></app-ng-style>`,
  styles: [
  ]
})
export class HomeComponent implements OnChanges {

  constructor() {}

ngOnChanges(){
  console.log("ngOnChanges");
}
```

#### ngOnInit
Se ejecuta una vez que Angular ha desplegado los data-bound properties(variables vinculadas a datos) o cuando el componente ha sido inicializado, una vez que ngOnChanges se haya ejecutado. Este evento es utilizado principalmente para inicializar la data en el componente.
```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-home',
  template: `
    <app-ng-style></app-ng-style>`,
  styles: [
  ]
})
export class HomeComponent implements OnInit {

  constructor() {}

ngOnInit(){
  console.log("ngOnInit");
}
```

#### ngDoCheck
Se activa cada vez que se verifican las propiedades de entrada de un componente. Este método nos permite implementar nuestra propia lógica o algoritmo de detección de cambios personalizado para cualquier componente.
```ts
import { Component, DoCheck } from '@angular/core';

@Component({
  selector: 'app-home',
  template: `
    <app-ng-style></app-ng-style>`,
  styles: [
  ]
})
export class HomeComponent implements DoCheck {

  constructor() {}

ngDoCheck(){
  console.log("ngDoCheck");
}
```

#### ngAfterContentInit
Se ejecuta cuando Angular realiza cualquier muestra de contenido dentro de las vistas de componentes y justo después de ngDoCheck. Actuando una vez que todas las vinculaciones del componente deban verificarse por primera vez. Está vinculado con las inicializaciones del componente hijo.
```ts
import { Component, AfterContentInit } from '@angular/core';

@Component({
  selector: 'app-home',
  template: `
    <app-ng-style></app-ng-style>`,
  styles: [
  ]
})
export class HomeComponent implements AfterContentInit {

  constructor() {}

ngAfterContentInit(){
  console.log("ngAfterContentInit");
}
```

#### ngAfterContentChecked
Se ejecuta cada vez que el contenido del componente ha sido verificado por el mecanismo de detección de cambios de Angular; se llama después del método ngAfterContentInit. Este también se invoca en cada ejecución posterior de ngDoCheck y está relacionado principalmente con las inicializaciones del componente hijo.
```ts
import { Component, AfterContentChecked } from '@angular/core';

@Component({
  selector: 'app-home',
  template: `
    <app-ng-style></app-ng-style>`,
  styles: [
  ]
})
export class HomeComponent implements AfterContentChecked {

  constructor() {}

ngAfterContentChecked(){
  console.log("ngAfterContentChecked");
}
```

#### ngAfterViewInit
Se ejecuta cuando la vista del componente se ha inicializado por completo. Este método se inicializa después de que Angular ha inicializado la vista del componente y las vistas secundarias. Se llama después de ngAfterContentChecked. Solo se aplica a los componentes.
```ts
import { Component, AfterViewInit } from '@angular/core';

@Component({
  selector: 'app-home',
  template: `
    <app-ng-style></app-ng-style>`,
  styles: [
  ]
})
export class HomeComponent implements AfterViewInit {

  constructor() {}

ngAfterViewInit(){
  console.log("ngAfterViewInit");
}
```

#### ngAfterViewChecked
Se ejecuta después del método ngAfterViewInit y cada vez que la vista del componente verifique cambios. También se ejecuta cuando se ha modificado cualquier enlace de las directivas secundarias. Por lo tanto, es muy útil cuando el componente espera algún valor que proviene de sus componentes secundarios.
```ts
import { Component, AfterViewChecked } from '@angular/core';

@Component({
  selector: 'app-home',
  template: `
    <app-ng-style></app-ng-style>`,
  styles: [
  ]
})
export class HomeComponent implements AfterViewChecked {

  constructor() {}

ngAfterViewChecked(){
  console.log("ngAfterViewChecked");
}
```

#### ngOnDestroy
Este método se ejecutará justo antes de que Angular destruya los componentes. Es muy útil para darse de baja de los observables y desconectar los event handlers para evitar memory leaks o fugas de memoria.
```ts
import { Component, OnDestroy } from '@angular/core';

@Component({
  selector: 'app-home',
  template: `
    <app-ng-style></app-ng-style>`,
  styles: [
  ]
})
export class HomeComponent implements OnDestroy {

  constructor() {}

ngOnDestroy(){
  console.log("ngOnDestroy");
}
```

## Servicios
Los servicios  son clases que se encargan de acceder a los datos para entregarlos a los componentes, lo bueno de esto es que se puede reaprovechar servicios para distintos componentes. Para la creación de servicios podemos usar el angular CLI o hacerlo manualmente creando una carpeta `service` dentro de app y creando nuestro archivo bajo la nomenclatura `name.service.ts`

```ts
import { Injectable } from '@angular/core';

@Injectable({providedIn: 'root'})
export class HeroesService {
    constructor() { }    
}
```
> El decorador `providedIn: 'root'` es una manera automática de importar servicios sin agregar al `app.module.ts`

Una vez creado el servicio debemos agregarlo en la sección providers del `app.module.ts`
```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { HeroesService } from "./service/heroes.service";

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [
    HeroesService
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
> **RECORDATORIO:** Si tenemos el decordar `providedIn: 'root'` en nuestro servicios, este paso de importarlo en el `app.module.ts` pasa a ser opcional.

Para hacer uso del servicio basta con importarlo e inyectarlo en el constructor de nuestro componente, como buena practica el nombre de la variable sera el mismo nombre de la clase pero antecediendole un `_`
```ts
import { Component, OnInit } from '@angular/core';
import { HeroesService, Heroe } from "../../service/heroes.service";

@Component({
  selector: 'app-heroes',
  templateUrl: './heroes.component.html',
  styles: [
  ]
})
export class HeroesComponent implements OnInit {
  public heroes: Heroe[] = [];
  constructor(private _heroesService: HeroesService) {}

  ngOnInit(): void {
    this.heroes = this._heroesService.getHeroes();
    console.log(this.heroes);
  }
}
```
> Los servicios tendran variables de tipo privadas y el tipo será del mismo que la clase importada

## Directivas
Las directivas son instrucciones para crear, formatear e interaccionar con el DOM. De hecho, los componentes son un tipo de directiva, ya que cuando usamos el selector de un componente, le estamos pidiendo a Angular que muestre dicho componente (y su lógica de programación) en algún lugar determinado del DOM. 

Al igual que existen directivas que son más habituales de usar creadas por el mismo angular como sería [ngIf](#ngif), [ngFor](#ngfor), [ngStyle](#ngstyle), [ngClass](#ngclass), etc... Existe la posibilidad de crear nuestras propias directivas con el comando `ng generate directive ruta`

```ts
import { Directive } from '@angular/core';

@Directive({
  selector: '[appResaltado]'
})
export class ResaltadoDirective {

  constructor() { console.log('Directiva personalizada') }
}
```

Podemos hacer uso de dicha directiva desde nuestro html llamándola en la etiqueta de nuestra preferencia
```html
<p appResaltado> Hola mundo</p>
```

Nuestra directiva podremos configurarla desde el archivo TS según la necesidad que tengamos importando las clases que requiramos a fin de modificar nuestro DOM.
```ts
import { Directive, ElementRef, HostListener } from '@angular/core';

@Directive({
  selector: '[appResaltado]'
})
export class ResaltadoDirective {

  // Evento que escucha cuando el mouse pasa por la etiqueta
  @HostListener('mouseenter') mouseEntro(){
    this.elementRef.nativeElement.style.backgroundColor = 'yellow';
  }

  // Evento que escucha cuando el mouse sale de la etiqueta
  @HostListener('mouseleave') mouseSalio(){
    this.elementRef.nativeElement.style.backgroundColor = null;
  }

  constructor(private elementRef:ElementRef) {}
}
```
De igual manera podremos mandar parámetros a nuestra directiva personalizada desde nuestro HTML, para ello basta con poner entre llaves nuestra directiva e igualarla con el parámetro a mandar, en nuestro archivo TS de nuestra directiva debemos usar el decorador [@Input](#input) a fin de recibir el parámetro a usar
```html
<p [appResaltado] = "'orange'">Hola mundo</p>
```
```ts
import { Directive, ElementRef, HostListener, Input,  } from '@angular/core';

@Directive({
  selector: '[appResaltado]'
})
export class ResaltadoDirective {

  @Input("appResaltado") nuevoColor:string

  @HostListener('mouseenter') mouseEntro(){
    this.resaltar(this.nuevoColor || 'yellow');
  }

  @HostListener('mouseleave') mouseSalio(){
    this.resaltar(null);
  }

  constructor(private elementRef:ElementRef) {}

  private resaltar (color:string){
    this.elementRef.nativeElement.style.backgroundColor = color;
  }
}
```


## Módulo
Los `módulos` son un mecanismos de agrupación lógica de símbolos (componentes, directivas, pipes y servicios) que permite a angular saber las importaciones / exportaciones necesarias para que cierto componente funcione. 
```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';

@NgModule({
  declarations: [],
  imports: [CommonModule]
})
export class ComponentsModule { }
```
Los módulos por defecto incluiran el decorador `@NgModule` e importarán el módulo opcional `CommonModule`.
> El `CommonModule` es un módulo básico de angular que incluira las directivas `NgIf, NgForOf, DecimalPipe, etc`



Un módulo Angular normalmente está formado por una carpeta completa de componentes, servicios, etc, al igual que también tienen la particularidad de definir las dependencias con otros módulos, esto ultimo es especialmente util ya que cuando queremos deshacernos de una funcionalidad de nuestra aplicación podríamos simplemente eliminar el Módulo Angular correspondiente, con un impacto mínimo en el resto de áreas de la aplicación.

```ts
@NgModule({
imports: [ BrowserModule, HttpModule, FormsModule ],
declarations: [ PersonComponent, ContactComponent, ContactListComponent ],
providers: [ PersonService, ContactService ],
exports: [ ContactListComponent, ContactComponent ]
})
export class ContactModule {}
```
Para poder usar los componentes/servicios/pipes, etc, en otros módulos debemos exportarlos dentro de nuestro decorador `@NgModule` e importar el módulo en el lugar correspondiente

```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { ContactModule } from '../contact.module';

@NgModule({
  declarations: [],
  imports: [
    CommonModule,
    ContactModule
    ]
})
export class ComponentsModule { }
```

## CommonModule
Módulo base de Angular proveniente del package `@angular/common` que exporta todas las directivas y Pipes de angular básicos, tales como `NgIf, NgForOf, DecimalPipe, etc`. Este módulo es reexportado por `BrowserModule`, que se incluye automáticamente en la raíz `AppModule` cuando se crea una nueva aplicación con el comando `new` en el CLI.
```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

@NgModule({
  declarations: [],
  imports: [BrowserModule],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

#### ngIf
Condicional del package `@angular/common` que permitira a través de su valor booleano ejecutar una sección del código HTML.

```html
<div *ngIf="false" class="card text-white bg-dark mb-3" style="width: 100%;">
    <div class="card-body">
        <h5 class="card-title">Fernando Antúnez</h5>
        <p class="card-text">Estudiar hasta tarde da frutos</p>                
    </div>
</div>
```

Este tipo de directiva condicionan eventos a fin de mostrar y/o eliminar elementos HTML.

<img src="img/ngIf-bandera.png" width="auto;"/>

```html
<div *ngIf="mostrar" class="card text-white bg-dark mb-3" style="width: 100%;">
  <div class="card-body">
      <h5 class="card-title">{{ frase.autor }}</h5>
      <p class="card-text">{{ frase.mensaje }}</p>
  </div>
</div>
<div class="d-grid gap-2">
    <button (click)="mostrar = !mostrar" class="bts btn-outline-dark btn-sm">
      Mostrar/Ocultar
    </button>
</div>
```
```ts
export class BodyComponent {
mostrar: boolean = true;
public frase : any = {
  mensaje: 'Estudiar hasta tarde da frutos',
  autor: 'Fernando Antúnez'
  }
}
```

#### ngFor
Condicional del package `@angular/common` que permitirá recorrer un arreglo. Se coloca en la etiqueta a repetir con la caracteristicas `*ngFor="let nombrePersonajes of personajes"` donde inicializamos una variable de nombre `nombrePersonajes` la cual tomará los elementos propios del arreglo `personajes`
```html
<ul class="list-group">
    <li *ngFor="let nombrePersonajes of personajes" class="list-group-item">
        {{ nombrePersonajes }}
    </li>
</ul>
```
```ts
export class BodyComponent {
  personajes : string[] = ['Spiderman', 'Venom', 'Dr. Octopus']
}
```
Dentro de la directiva `ngFor` podemos agregar código adicional separandolos con un `;` como sería el `index`
<img src="img/ngfor-array.png" width="auto;"/>
```html
<ul class="list-group">
    <li *ngFor="let nombrePersonajes of personajes; let i = index" class="list-group-item">
        {{ i + 1 }} - {{ nombrePersonajes }}
    </li>
</ul>
```  

#### ngStyle
Una directiva de atributo que actualiza los estilos del elemento HTML que lo contiene desde el `component.ts`. Establece una o más propiedades de estilo, especificadas como pares clave-valor separados por dos puntos.

```ts
const styleExp: string = '40px'
const widthExp: number = 40;
const objExp: object = {
  'font-size': '15px',
  'color': 'red',
  'background-color': 'blue'
}

//Establece la fuente del elemento contenedor en el resultado de
//una expresión (styleExp).
<p [ngStyle]="{'font-size': styleExp}">A
</p>

//Establece el ancho del elemento contenedor en un valor de píxel
//devuelto por una expresión (widthExp).
<p [ngStyle]="{'max-width.px': widthExp}">E
</p>

//Establece una colección de valores de estilo mediante una
//expresión que devuelva pares clave-valor (objExp).
<p [ngStyle]="objExp">I
</p>
```

#### ngClass
Agrega y elimina clases CSS en un elemento HTML, su sintasis básica es escribir la propiedad `[ngClass]` seguida de la clase tipo string o variable que la acompañe. Las clases CSS se actualizan de la siguiente manera, según el tipo de evaluación de la expresión:

*   **`string`:** se agregan las clases CSS enumeradas en la cadena (delimitadas por espacios). Estas clases pueden venir escritas entre comillas simples dentro del `ngClass` o llamadas desde el `component.ts` desde alguna variable
    ```html
    <p [ngClass]="'first second'">...</p>
    <p [ngClass]="variable|stringExp|arrayExp|objExp">...</p>
    ```
*   **`Array`:** se agregan las clases CSS declaradas como elementos Array.
    ```html
    <p [ngClass]="['first', 'second']">...</p>
    ```
*   **`Object`:** las claves son clases CSS que se agregan cuando la expresión dada en el valor se evalúa como un valor `true`, de lo contrario, se eliminan.
    ```html
    <p [ngClass]="{'first': true, 'second': true, 'third': false}">...</p>
    <p [ngClass]="{'class1 class2 class3' : true}">...</p>
    ```

Otra manera de escribir clases en angular de manera dinamica es agregando entre corchetes la propiedad `[class]` seguida del nombre de la clase.
```ts
change = true;
```
```html
<p [class.isValid]="change">Validamos la clase</p>
```
En este caso usamos el booleano change para mostrar y ocultar la clase `isValid`


#### ngSwitch
La directiva ngSwitch es una directiva de atributo que evalúa una determinada variable. La misma se usa con otras 2 directivas:
* **`ngSwitchCase`**: Permite mostrar un elemento HTML dependiendo del valor de la variable evaluada en la directiva ngSwitch.
* **`ngSwitchDefault`**: Mostrará un elemento HTML en el caso de que no se muestre ningún ngSwitchCase. Esta directiva debe colocarse al final de todos los ngSwitchCase.


```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-ng-switch',
  templateUrl: './ng-switch.component.html',
  styles: [
  ]
})
export class NgSwitchComponent {
  alerta:string = 'info';
  constructor() { }
}
```
```html
<!--Evalua el elemento 'alerta'-->
<div [ngSwitch]="alerta">
    <div *ngSwitchCase="'success'">success</div>
    <div *ngSwitchCase="'info'">info</div>
    <div *ngSwitchCase="'warning'">warning</div>
    <div *ngSwitchDefault>danger</div>
</div>
```

## Navegación en Angular
La navegación en angular se basa en disminuir en lo posible la cantidad de data a intercambiar entre el **browser** y el **servidor**, para ello que hace es cargar una sola página (generalmente **index.html**) y después, todas las otras páginas/componentes se refrescan usando **Javascript**; pero sólo **index.html** es una página completa, el resto de las páginas son sólo porciones de HTML que su código Javascript va cambiando **dinámicamente**.

#### Routes File
Para el manejo de la navegación de las rutas creamos un archivo de nombre `app.routes.ts` dentro de la carpeta `app`, dicho archivo estará compuesto por una constante de tipo `Routes` que poseerá todos las rutas a navegar
```ts
import { Routes, RouterModule } from '@angular/router';
import { NgModule } from '@angular/core';
import { HeroesComponent } from './components/heroes/heroes.component';

const ROUTES: Routes = [
    { path: 'home', component: HomeComponent },
    { path: '**', pathMatch:'full', redirectTo: 'home'}
];

@NgModule({
    imports: [RouterModule.forRoot(ROUTES)],
    exports: [RouterModule]
})
export class AppRoutesModule {}
```
>    Utilizaremos el path `{ path: '**', pathMatch:'full', redirectTo: 'home'}`, para generar una ruta por defecto en caso que la ruta colocada no exista, el mismo siempre se debe colocar al final de todas las rutas.

Este módulo debe ser importado en el archivo base `app.modules.ts`
```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppRoutesModule  } from "./app.routes";

@NgModule({
  declarations: [],
  imports: [
    BrowserModule,
    AppRoutesModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
Para poder renderizar la web indicada por la ruta debemos agregar la etiqueta `router-outlet`donde deseemos que se valla a renderizar las rutas, en este caso lo haríamos en `app.component.html`
```html
<app-navbar></app-navbar>
<router-outlet></router-outlet>
```
Otro método para generar las rutas es generar el código directamente desde desde el archivo `app.module.ts`, es decir en nuestro archivo de rutas tendríamos algo como
```ts
import { Routes } from '@angular/router';
import { HomeComponent } from './components/home/home.component';
export const ROUTES: Routes = [
    { path: 'home', component: ArtistaComponent },
    { path: '', component: HomeComponent },
    { path: '**', component: HomeComponent }
];
```
Mientras que en nuestro `app.module.ts` importariamos la librería `RouterModule` de angular y el archivo `app.route.ts` que creamos.
```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { RouterModule } from "@angular/router";

import { AppComponent } from './app.component';
import { HomeComponent } from './components/home/home.
import { ROUTES } from "./app.routes";

@NgModule({
  declarations: [
    AppComponent,
    HomeComponent
  ],
  imports: [
    BrowserModule,
    RouterModule.forRoot(ROUTES, {useHash:true})
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
> El `{ useHash: true }`, permitirá que la ruta del proyecto a mostrar incluya un `#` dando como resultado `http://localhost:4200/#/home`

#### RouterModule.forRoot vs RouterModule.forChild
Al momento de inyectar las configuraciones en nuestro archivo de rutas nos toparemos con 2 métodos a importar, el `forRoot()` y `forChild()`
Utilizaremos el método `forRoot()` cuando estemos úbicados en el módulo principal de la APP por lo general llamado `AppRoutingModule`, este módulo contiene  todas las directivas, las rutas, y el propio servicio del router, en pocas palabras es el primer módulo que se carga cuando se ejecuta la aplicación por primera vez 
```ts
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';

const routes: Routes = [
  { path: '', component: HomeComponent }
];

@NgModule({
  //Sección a usar forRoot() o forChild()
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}
```
Utilizaremos `forChild()` al momento de crea módulos hijos con sus propios archivos de rutas, este tipo de modalidad de trabajo es de suma importancia cuando tenemos aplicaciones muy grande ya que permite la carga bajo demanda o [Lazy Loading](#lazy-loading)
> **NOTA:** Los siguientes archivos de `AmericaRoutingModule` y `EuropaRoutingModule` serán referenciados en la sección de [Lazy Loading](#lazy-loading)
```ts
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { EspanaComponent } from './espana/espana.component';
import { FranciaComponent } from './francia/francia.component';
import { ItaliaComponent } from './italia/italia.component';


const routes: Routes = [
  {
    path: 'espana',
    component: EspanaComponent
  },
  {
    path: 'francia',
    component: FranciaComponent
  },
  {
    path: 'italia',
    component: ItaliaComponent
  } 
];

@NgModule({
  imports: [RouterModule.forChild(routes)],
  exports: [RouterModule]
})
export class EuropaRoutingModule { }
```
```ts
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { ChileComponent } from './chile/chile.component';
import { ArgentinaComponent } from './argentina/argentina.component';
import { UruguayComponent } from './uruguay/uruguay.component';

const routes: Routes = [
  {
    path: 'chile',
    component: ChileComponent
  },
  {
    path: 'argentina',
    component: ArgentinaComponent
  },
  {
    path: 'uruguay',
    component: UruguayComponent
  }  
];

@NgModule({
  imports: [RouterModule.forChild(routes)],
  exports: [RouterModule]
})
export class AmericaRoutingModule { }
```

#### Lazy Loading
El Lazy Loading o carga perezosa nos permite organizar una aplicación Angular a fin que la misma no cargue en forma completa toda la aplicación web en una única llamada al servidor, sino que retrace la carga hasta el momento de su utilización (carga bajo demanda).
Esta forma de particionar una aplicación y su carga por partes es de suma importancia cuando tenemos aplicaciones muy grandes y tiene como beneficio que el usuario no tenga que esperar mucho tiempo en la carga inicial de la aplicación. Como desventaja podríamos decir que cuando el usuario accede a otras secciones de la aplicación también tenga que esperar que se recuperen del servidor.
Para simular un Lazy Loading, continuaremos con los archivos routing usados en [RouterModule.forRoot vs RouterModule.forChild](#routermoduleforroot-vs-routermoduleforchild). Acá tendremos 2 módulos (`AmericaModule` & `EuropaModule`) que alojaran sus clases especificas y donde cada módulo administrará las rutas hijas anterioremente creadas
```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';

@NgModule({
  declarations: [],
  imports: [
    CommonModule,
    AmericaRoutingModule
  ]
})
export class AmericaModule { }
```
```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';

@NgModule({
  declarations: [],
  imports: [
    CommonModule,
    EuropaRoutingModule
  ]
})
export class EuropaModule { }
```
> Es importan recordar importar estas rutas hijas

Después de crear nuestro módulos hijos procedemos a codificar las rutas del módulo principal de nuestra aplicación, para ello abrimos el archivo `app-routing.module.ts` y especificamos la sintaxis para hacer la carga de los otros módulos con Lazy Loading:

```ts
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { AmericaComponent } from './america/america.component';
import { EuropaComponent } from './europa/europa.component';

const routes: Routes = [
  {
    path: 'america',
    component: AmericaComponent,
    loadChildren: () => import('./america/america.module').then(m => m.AmericaModule)
  },
  {
    path: 'europa',
    component: EuropaComponent,
    loadChildren: () => import('./europa/europa.module').then(m => m.EuropaModule)
  }
]

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```
Podemos ver que la sintaxis para la carga diferida usa la propiedad `loadChildren` seguida de la función `import` para las importaciones dinámicas del módulo indicado en el parámetro. La ruta de importación es la ruta relativa al módulo:
```ts
loadChildren: () => import('./america/america.module').then(m => m.AmericaModule)
```

#### RouterLink y RouterLinkActive
El `RouterLink` es una directiva que permite la navegación entre las distintas rutas de nuestra app, la misma se colocará en nuestro archivo HTML de la siguiente manera
```html
<ul class="navbar-nav mr-auto">
    <li class="nav-item">
        <a class="nav-link" [routerLink]="['home']">Home</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" routerLink="heroes">Heroes</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" [routerLink]="['about']">About</a>
    </li>
</ul>
```
El router link se puede con o sin corchetes, la diferencia principal entre ambos es que sin corchetes estaríamos pasando una cadena de caracteres, es decir un valor no modificable, mientras que con corchete se puede pasar tanto una propiedad como diversos parametros en caso de ser necesario
```html
<ul class="navbar-nav mr-auto">
    <li class="nav-item">
        <a class="nav-link" [routerLink]="routerLinkVariable">Home</a>
    </li>
    <li class="nav-item" routerLinkActive="active">
        <a class="nav-link" [routerLink]="[routerLinkVariable,routerLinkDynamicParameter]">Home2</a>
    </li>
</ul>
```
```ts
export class NavbarComponent  {
  public routerLinkVariable= "/home";
  public routerLinkDynamicParameter= 123;

  updateRouterLinkVariable(){
    this.routerLinkVariable="/about";
  }
}
```
En el caso del `home2` la ruta que estaríamos pasando al hacer click sería del tipo `http://miruta/home/123`. 


El `RouterLinkActive` es una propiedad que va a permitir colocar la(s) clase(s) que se estipulen dentro del elemento siempre que exista un elemento hijo de tipo `RouterLink` al cual se le de click
```html
<ul class="navbar-nav mr-auto">
    <li class="nav-item" routerLinkActive="active">
        <a class="nav-link" [routerLink]="['/home']">Home</a>
    </li>
    <li class="nav-item" routerLinkActive="active">
        <a class="nav-link" [routerLink]="['/heroes']">Heroes</a>
    </li>
    <li class="nav-item" routerLinkActive="active">
        <a class="nav-link" [routerLink]="['/about']">About</a>
    </li>
</ul>
```
En este caso al dar click a `home` el `routerLinkActive` agregará la clase `active` a la etiqueta `<li>` donde se encuentra.

#### Router
Las navegación entre las rutas pueden venir dadas a través del html con el `RouterLink` anteriormente mencionado o desde el TS importando la librería `Router` de angular

```ts
import { Component } from '@angular/core';
import { Router } from "@angular/router";

@Component({
  selector: 'app-heroes',
  templateUrl: './heroes.component.html'
})
export class HeroesComponent {
  constructor(private router:Router) {}

  navergarHome(){
    this.router.navigate(['/home']);
  }
}
```
```html
<div>
      <button (click)="navergarHome()" type="button">Navegar Home</button>
</div>
```
La propiedad `navigate` recibirá un arreglo igual al mandado en el `RouterLink`.
Para la navegación enviando parametros se aplicaría la misma lógica, es decir puede ser desde el HTML con `[routerLink]="[ruta,parametros]"`
```html
<div class="card-columns">
  <div class="card animated fadeIn fast" *ngFor="let heroe of heroes; let i = index">
    <img [src]="heroe.img" class="card-img-top" [alt]="heroe.nombre">
    <div class="card-body">
      <h5 class="card-title">{{heroe.nombre}}</h5>
      <p class="card-text">{{ heroe.bio }}</p>
      <p class="card-text"><small class="text-muted">{{ heroe.aparicion }}</small></p>
      <a [routerLink]="['/heroe',i]" class="btn btn-outline-primary btn-block">Ver más link...</a>
      <button (click)="verHeroe(i)" type="button" class="btn btn-outline-primary btn-block">Ver más desde TS...</button>

    </div>
  </div>
</div>
```
O por el otro lado desde el TS con el evento click más la función `(click)="verHeroe(i)"`

```ts
import { Component, OnInit } from '@angular/core';
import { HeroesService, Heroe } from "../../service/heroes.service";
import { Router } from "@angular/router";

@Component({
  selector: 'app-heroes',
  templateUrl: './heroes.component.html',
  styles: [
  ]
})
export class HeroesComponent implements OnInit {
  public heroes: Heroe[] = [];
  constructor(private _heroesService:HeroesService, 
    private router:Router) {}

  ngOnInit(): void {
    this.heroes = this._heroesService.getHeroes();    
  }

  verHeroe(idx:number){
    this.router.navigate(['/home']);
  }
}
```

Para toda navegación es importante colocar el `/` en la ruta a fin de movernos a la raíz debido a que podemos conseguir errores dentro del `router-outlet` del tipo que concatenan parametros entre rutas, por ejemplo si estamos en una subpágina `http://miruta/heroes` y damos click al hipervinculo
```html
<a [routerLink]="['heroe',i]" class="btn btn-outline-primary">Ver más...</a>
```
La ruta final que se obtendra sera del tipo `http://miruta/heroes/heroe/1` ya que no nos redirgimos a la ráiz, por ello el la ruta correcta a enviar sería `[routerLink]="['/heroe',i]"`

#### ActivatedRoute
En muchas ocasiones tendremos que utilizar/recuperar los parámetros enviados mediante el sistema de rutas, para recibir los valores de los parámetros en el componente al que nos dirige la ruta tenemos que usar un objeto del sistema de routing llamado `ActivatedRoute`. Este objeto nos ofrece diversos detalles sobre la ruta actual, entre ellos los parámetros que contiene. Para usarlo debemos importarlo de su librería `@angular/router` e inyectarlo en el constructor
```ts
import { Component } from '@angular/core';
import { ActivatedRoute } from "@angular/router";

@Component({
  selector: 'app-artista',
  templateUrl: './artista.component.html',
  styles: []
})
export class ArtistaComponent {

  constructor(private activateRouter:ActivatedRoute) { 
    this.activateRouter.params.subscribe(newParams =>{
      console.log(newParams['id']);      
    })
   }
}
```
En este ejemplo al objeto de tipo `AtivatedRoute` usa una propiedad llamada `params` que es un observable el cuál a través del método `suscribe()` nos permitirá estar atento a los cambios en los parámetros enviados al componente. Podemos usar los [Operadores RxJS.](#operadores-rxjs)

Para obtener los parametros del las rutas padres al momento de usar [rutas anidadas o rutas hijas](#rutas-anidadas), basta con estar dentro del componente hijo y usar la misma sintaxis anteriormente usada pero agregando la propiedad `parent` quedando de la siguiente manera.
```ts
this.activatedRoute.parent.params.subscribe(data =>{
  console.log(data)
}
```

#### Rutas Anidadas 
Las rutas anidadas o rutas hijas son rutas que por cuestiones de usabilidad anidamos a las navegaciones a fin de no perder/recargar la información obtenida por la ruta padre. Por ejemplo, en una subpágina de `usuarios` deseamos mostrar multiple información del mismo, para ello debemos dirigirnos a nuestro archivo de rutas y en el `path` del usuario agregamos la propiedad `children` el cual es un arreglo de rutas
```ts
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './components/home/home.component';
import { UsuarioDetalleComponent } from './components/usuario/usuario-detalle.component';
import { UsuarioEditarComponent } from './components/usuario/usuario-editar.component';
import { UsuarioNuevoComponent } from './components/usuario/usuario-nuevo.component';
import { UsuarioComponent } from './components/usuario/usuario.component';


const ROUTES: Routes = [
    { path: 'home', component: HomeComponent },
    {
        path: 'usuario/:id', component: UsuarioComponent, children: [
            { path: 'nuevo', component: UsuarioNuevoComponent },
            { path: 'detalle', component: UsuarioDetalleComponent },
            { path: 'editar', component: UsuarioEditarComponent }
        ]
    },
    { path: '**', pathMatch: 'full', redirectTo: 'home' }
];

@NgModule({
    imports: [RouterModule.forRoot(ROUTES)],
    exports: [RouterModule]
})
export class AppRoutingModule { }
```
Para renderizar las rutas hijas debemos agregar la etiqueta `router-outlet` en el HTML del componente padre
```html
<router-outlet></router-outlet>
```
En caso de desear renderizar una ruta hija por default basta con colocar el `path '**'` a nuestras rutas hijas
```ts
const ROUTES: Routes = [
    { path: 'home', component: HomeComponent },
    {
        path: 'usuario/:id', component: UsuarioComponent, children: [
            { path: 'nuevo', component: UsuarioNuevoComponent },
            { path: 'detalle', component: UsuarioDetalleComponent },
            { path: 'editar', component: UsuarioEditarComponent },
            { path: '**', pathMatch: 'full', redirectTo: 'nuevo' }
        ]
    },
    { path: '**', pathMatch: 'full', redirectTo: 'home' }
];
```
Cuando existen una gran cantidad de rutas hijas es más practico crear un archivo personalizado de solo las rutas y luego exportarla en nuestro `app.route.ts`
```ts
import { Routes } from '@angular/router';
import { UsuarioDetalleComponent } from './usuario-detalle.component';
import { UsuarioEditarComponent } from './usuario-editar.component';
import { UsuarioNuevoComponent } from './usuario-nuevo.component';

export const USUARIO_ROUTES: Routes = [
    { path: 'nuevo', component: UsuarioNuevoComponent },
    { path: 'detalle', component: UsuarioDetalleComponent },
    { path: 'editar', component: UsuarioEditarComponent },
    { path: '**', pathMatch: 'full', redirectTo: 'nuevo' }    
];
```
Dando como resultado un path del tipo
```ts
{ path: 'usuario/:id', component: UsuarioComponent, children: USUARIO_ROUTES},
```
En caso de desear obtener los parametros enviados por el padre dentro de una ruta hija debemos hacer uso del [ActivatedRoute](#activatedroute) 


## Decoradores
Un decorador es una clase especial de declaración que puede acoplarse a una clase, método, propiedad o parámetro y extiende una función agregandole información y funcionalidad. Los decoradores se reconocen ya que inician con un `@` y se expresan de la siguiente manera
```ts
@decorador
clase/método/propiedad/parámetro
```

#### @Input
Los decoradores Input son una clase que permite pasar parametros desde el componente padre al hijo, para poderlo utilizar debemos importar en el componente hijo el decorador `Input` que se encuentra en `@angular/core` y colocar el decorar `@Input()` a la propiedad que se podra manipular desde el padre

```ts
import { Component, Input} from '@angular/core';

@Component({
  selector: 'app-heroe-tarjeta',
  templateUrl: './heroe-tarjeta.component.html'
})
export class HeroeTarjetaComponent {
  @Input() public heroeTarjeta: string = '';

  constructor() {}
}
```
> Podemos colocarle valores predeterminados a la propiedad de modo que si no se entrega un valor asumiría que debe usar ese.
`@Input() nombre = 'valor de la propiedad';`

Para poder hacer uso de las propiedades de los Input desde el componente padre debemos llamarla y/o asignarles valores dentro de las etiquetas html del padre

```html
  <app-heroe-tarjeta [heroeTarjeta]="valor a mandar">
  </app-heroe-tarjeta>
```
> La propiedad puede recibir cualquier tipo de valor, bien sea proveniente de otras variables, funciones, etc.



#### @Output
Los decoradores Output son una clase que permite pasar parametros desde el componente hijo al padre, para poderlo utilizar debemos importar en el componente hijo el decorador `Output` y el `EventEmitter` que se encuentra en `@angular/core` y colocar el decorar `@Output()` a la propiedad que se podra manipular desde el padre la cual sera del tipo `EventEmitter<Tipo>`

```ts
import { Component, Output, EventEmitter } from '@angular/core';
import { Router } from '@angular/router';

@Component({
  selector: 'app-heroe-tarjeta',
  templateUrl: './heroe-tarjeta.component.html'
})
export class HeroeTarjetaComponent  {
  @Output() hereoSeleccionado: EventEmitter<number>;

  constructor() {
    this.hereoSeleccionado = new EventEmitter();
  }

  verHeroe(){
    this.hereoSeleccionado.emit(this.index);
  }
}
```
Toda propiedad de tipo `EventEmitter` debe ser inicializada desde el constructor y dicha propiedad tendra un método `emit` el cual enviará la información indicada al componente padre.
Para poder recibir los datos desde el componente padre debemos llamar la propiedad del hijo colocandola entre parentesis e igualarla a la propiedad/función propia del padre que requiramos usar. Para recibir el evento o valor emitido del componente hijo vamos a usar la palabra reservada `$event`
```html
    <app-heroe-tarjeta (hereoSeleccionado)="verHeroe($event)">
    </app-heroe-tarjeta>
```

## Guard
Los Guards en Angular, son middlewares que se ejecutan antes de cargar una ruta y determinan si se puede cargar dicha ruta o no, es especialmente util ya que evitamos que los usuarios vean una interfaz a la que no tienen acceso

* **CanActivate:** Mira si el usuario puede acceder a una página determinada.
* **CanActivateChild:** Mira si el usuario puede acceder a las páginas hijas de una determinada ruta.
* **CanLoad:** Antes de cargar los recursos `assets` de la ruta.
* **CanDeactivate:** Antes de intentar salir de la ruta actual, usualmente utilizado para evitar salir de una ruta, si no se han guardado los datos.

```ts
import { Injectable } from '@angular/core';
import { CanActivate, ActivatedRouteSnapshot, RouterStateSnapshot, UrlTree } from '@angular/router';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root'
})
export class AuthGuard implements CanActivate {
  canActivate(
    next: ActivatedRouteSnapshot,
    state: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {
    return true;
  }
}
```
Como middleware, estos componentes se ejecutan de manera intermedia antes de determinadas acciones y si retorna `true` la ruta seguiría su carga normal, en caso negativo, el Guard retornaría `false` y la ruta no se cargaría.`
Para poder usar los guards debemos importarlos en la sección de `providers` en nuestro `app.module.ts` y agregarlo en nuestro archivo de rutas, en las ruta(s) que lo requieran
```ts
providers: [AuthGuard]
```
```ts
{path:'home', component: HomeComponent, canActivate:[AuthGuard]}
```

## Pipes
Los pipes son herramientas de Angular que nos permitirán transformar visualmente la información (no cambián el valor de la misma), entre los pipes tenemos:

#### Uppercase
Transforma todo el texto a mostrar a mayúscula
```ts
value_expression = "Hola Mundo";
{{ value_expression | uppercase }}
resultado = HOLA MUNDO ;
```

#### Lowercase
Transforma todo el texto a mostrar a minúscula
```ts
value_expression = "Hola Mundo";
{{ value_expression | lowercase }}
resultado = hola mundo ;
```

#### Slice
Permite cortar un texto/arreglo creando así un nuevo valor desde el punto cortado.
```ts
value_expression = "Hola Mundo";
{{ value_expression | slice:3 }}
resultado = a mundo ;
```
También podemos pasar los puntos de inicio y fin del parámetro que que deseamos cortar.
```ts
value_expression = "Hola Mundo";
{{ value_expression | slice:0:3 }}
resultado = hol ;
```
En los arreglos ocurriría igual, podemos pasar la posición de incio y final que deseamos traer.
```ts
value_expression = [1,2,3,4,5,6,7,8,9];;
{{ value_expression | slice:1:5 }}
resultado = 2,3,4,5 ;
```

#### Decimal
Permite formatear un valor tipo number con las reglas que se le estipulen. Siguen los siguientes parametros `{{ value_expression | number [ : digitsInfo [ : locale ] ] }}`
Donde los parámetros de `digitsInfo` vendrá escrito bajo el siguiente formato:
`{minIntegerDigits}.{minFractionDigits}-{maxFractionDigits}`
* **minIntegerDigits:** Es el número mínimo de dígitos enteros antes del punto decimal. El valor predeterminado es 1.
* **minFractionDigits:** El número mínimo de dígitos después del punto decimal. El valor predeterminado es 0.
* **maxFractionDigits:** El número máximo de dígitos después del punto decimal. El valor predeterminado es 3.

```ts
value_expression = Math.PI;
{{ value_expression | number:'1.0-3' }}
resultado = 3.142;

value_expression = Math.PI;
{{ value_expression | number:'3.0-3' }}
resultado = 003.142;

value_expression = Math.PI;
{{ value_expression | number:'.0-2' }}
resultado = 3.14;
```
> Si no colocamos un `minIntegerDigits` angular traerá todos los números enteros que halle.

#### Percent
Permite formatear un valor a una cadena de porcentaje, según las reglas estipuladas. Siguen los siguientes parametros `{{ value_expression | percent [ : digitsInfo [ : locale ] ] }}`

```ts
value_expression = 0.234;
{{ value_expression | percent }}
resultado = 23%;

value_expression = 0.234;
{{ value_expression | percent:'2.2-2' }}
resultado = 23.40%;
```
Las reglas estipuladas siguen las mismas normas que las estipuladas en el pipe `Decimal`

#### Currency
Permite formatear un valor a una cadena de moneda, según las reglas estipuladas. Siguen los siguientes parametros `{{ value_expression | currency [ : currencyCode [ : display [ : digitsInfo [ : locale ] ] ] ] }}`

```ts
value_expression = 1234.5;
{{ value_expression | currency }}
resultado = $1234.5;

value_expression = 1234.5;
{{ value_expression | currency:'EUR' }}
resultado = €1234.5;

value_expression = 1234.5;
{{ value_expression | currency:'CAD$ ':'symbol':'.0-0' }}
resultado = CAD$ 1234.5;

value_expression = 1234.5;
{{ value_expression | currency:'LTM ':'symbol':'.0-0' }}
resultado = LTM 1234.5;
```
Las reglas estipuladas permiten personalizar la moneda a mostrar en caso de ser necesario como ocurre con la moneda inventada `LTM`


#### Json
Permite convertir un objeto en su representación tipo JSON para mostrar

```ts
value_expression = {nombre:'Logan', clave:'Wolverine', edad:500,
  direccion:{calle:'Primera',casa:20}};
{{ value_expression }}
resultado = [object Object];

value_expression = {nombre:'Logan', clave:'Wolverine', edad:500,
  direccion:{calle:'Primera',casa:20}};
{{ value_expression | json }}
resultado = { "nombre": "Logan", "clave": "Wolverine", "edad": 500, "direccion": { "calle": "Primera", "casa": 20 } };
```
Si deseamos que el resultado se mire más ordenado podemos usar la etiqueta HTML `<pre></pre>`.
```html
<pre>
  {{ heroe | json }}
</pre>    
```
El cual nos mostrará como resultado, es decir una información más ordenada y facil de leer.
```json
          {
  "nombre": "Logan",
  "clave": "Wolverine",
  "edad": 500,
  "direccion": {
    "calle": "Primera",
    "casa": 20
  }
} 
```

#### Async

Permite resolver situaciones de programación asíncrona desde el HTML

```ts
value_expression = new Promise<string>((resolve) => {
                          resolve('llego la data');
                      });
{{ value_expression }}
resultado = [object Promise];

value_expression = new Promise<string>((resolve) => {
                          resolve('llego la data'); 
                      });
{{ value_expression | async }}
resultado = 'llego la data';
```
En caso de existir un error o entrar en el `reject` la data no se mostrará salvo que se haya trabajado previamente el `catch`

#### Date

Permite formatear un valor de fecha con las reglas configuradas
`{{ value_expression | date [ : format [ : timezone [ : locale ] ] ] }}`

```ts
value_expression = new Date();
{{ value_expression }}
resultado = Thu Apr 29 2021 20:07:39 GMT-0400 (hora de Venezuela);

value_expression = new Date();
{{ value_expression | date }}
resultado = Apr 29, 2021;

value_expression = new Date();
{{ value_expression | date:'medium' }}
resultado = Apr 29, 2021, 8:10:04 PM;

value_expression = new Date();
{{ value_expression | date:'short' }}
resultado =  4/29/21, 8:10 PM;
```
Angular trae por default varias opciones predefinidas para el formateo de fecha como sería en el caso de `medium`, `short`, etc. Si deseamos colocar un formato personalizado debemos colocarlo entre comillas simples después del `date` siguiendo las configuraciones encontradas en la documentación de angular

```ts
value_expression = new Date();
{{ value_expression | date:'MMMM - dd' }}
resultado = April - 29;
```
Por defecto el idioma en el cual se mostrarán las fechas sera el ingles, si deseamos cambiar o agregar otros idiomas debemos de agregar librerías de dichos idiomas ejecutando `ng add @angular/localize` e importando en el `app.module.ts`
```ts
import { LOCALE_ID } from '@angular/core';
// la terminación es según el idioma en este caso es=español
import '@angular/common/locales/global/es';

providers: [
    { provide: LOCALE_ID, useValue: 'es' }    //linea agregada
  ],
```
Después de agregar dichas dependencias la app tomará como lenguaje principal el asignado en el `providers`, de forma adicional podemos importar más idiomas y usarlos en la opción local de nuestro pipe, por ejemplo si importamos el frances `import '@angular/common/locales/global/fr'` y agregamos como opción de date `fr` nos quedaría
```ts
value_expression = new Date();
{{ value_expression | date:'MMMM - dd':'':'fr }}
resultado = avril - 30;
```

#### Personalizado
Los pipes personalizados pueden ser creado mediante Angular CLI con el comando `ng g p ruta` los cuales por buenas practicas se suelen crear en una carpeta de nombre **pipes**, si usamos el comando `ng g p pipes/capitalizado` nos creará en la ruta `src/app/pipes`
* **capitalizado.pipe.spec.ts**: archivo de pruebas del pipe
* **capitalizado.pipe.ts**: archivo de configuración del pipe

De manera adicional nos actualizará las declaraciones con el nuevo elemento agregado en el `app.module.ts`, el pipe creado nos generará un archivo TS del tipo
```ts
import { Pipe, PipeTransform } from '@angular/core';
@Pipe({
  name: 'capitalizado'
})
export class CapitalizadoPipe implements PipeTransform {

  transform(value: unknown, ...args: unknown[]):unknown {  
    return null;
  }
}
```
Donde `value` representará el valor enviado desde el pipe en el html, mientras que `...args` recibirá la cantidad de argumentos que se deseen enviar
```ts
value_expression = 'fErNaNdO';
{{ value_expression | capitalizado:1:true:'Hola'}}
value = 'fErNaNdO'
...args= [1,true,'Hola'];
```
De igual forma podemos atrapar los argumentos desde el pipe, por ejemplo si enviamos los mismos argumentos anteriores podemos indicarle lo que recibirá y el tipo
```ts
transform(
  value: unknown, 
  edad: number, 
  activo:boolean, 
  mensaje: string):unknown {  
  return null;
}
```

El decorador `@Pipe` recibe multiples propiedades entre ellas tenemos
```ts
@Pipe({
  name: 'capitalizado',
  pure: false
})
```
>**name:** Nombre del pipe
>**pure:** Por default no se coloca y viene seteada en `true`, pero al cambiarla a `false` detectará los cambios impuros dentro de un objeto compuesto, es decir con esto angular activará la detección de cambios a la propiedad marcada.
#### DomSeguro
Existen enlaces, css, img, etc que nuestra app las detectará como inseguras prohibiendo abrirla, si nosotros estamos seguros de la procedencia de estos archivos podemos crear un pipe que nos permita pasar estos datos por algún sanitazer o función que nos permita limpiar/permitir el uso de dichos archivos, para ellos usaremos la clase de angular `DomSanitizer`.
```ts
import { Pipe, PipeTransform } from '@angular/core';
import { DomSanitizer, SafeResourceUrl } from '@angular/platform-browser';
@Pipe({
  name: 'domseguro'
})
export class DomseguroPipe implements PipeTransform {
  constructor(private domSanitizer:DomSanitizer) {}

  transform(value: string): SafeResourceUrl {
    return this.domSanitizer.bypassSecurityTrustResourceUrl(value);
  }
}
```
## Peticiones HTTP
La mayoría de las aplicaciones front-end necesitan comunicarse con un servidor a través del protocolo HTTP para descargar o cargar datos y acceder a otros servicios back-end. Para usar el cliente HTTP de angular para hacer peticiones y consumir API REST usando los distintos métodos (GET, POST, PUT, DELETE, etc), es necesario importar el módulo propio de angular `HttpClientModule` en el `app.module.ts`
```ts
import { HttpClientModule } from "@angular/common/http";

@NgModule({
  declarations: [AppComponent],
  imports: [
    BrowserModule,
    HttpClientModule,
    RouterModule.forRoot(ROUTES, {useHash:true})
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
Seguido de esto importamos la clase `HttpClient` de `@angular/common/http` en el componente/servicio donde lo vallamos a utilizar y lo inyectamos a su constructor 
```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';

@Injectable()
export class ConfigService {
  constructor(private http: HttpClient) { }
}
```
La clase `HttpCliente` nos traerá los distintos métodos (GET, POST, PUT, DELETE) los cuales usaremos para relizar las peticiones
```ts
url = 'https://restcountries.eu/rest/v2/lang/es'
params = {name:'Fernando'}
// Get
this.http.get(url)
// Post
this.http.post(url, params)
//Put
this.http.put(url, params)
// Delete
this.http.post(url+'?id')
```
Estas peticiones devolveran un Observable con el tipo de dato que se le indiquen, por lo que es recomendable indicarlo en la función que llamará la petición
```ts
getProductos(): Observable<any>{
    return this.http.get(this.url+'productos');
}
```

#### GET
El método `GET` solicita una representación de un recurso específico. Las peticiones que usan el método GET sólo deben recuperar datos.

#### POST
El método `POST` se utiliza para enviar una entidad a un recurso en específico, causando a menudo un cambio en el estado o efectos secundarios en el servidor.
En angular un petición de tipo `POST` se compone de:
*   **`url`:** Sera de tipo `string` y representará endpoint a usar.
*   **`body`:** Puede ser de tipo `any` o de algún tipo que se le especifique en concreto (Por lo general suele ser un objeto) donde se almacenará la data. 
*   **`options`:** Es un objeto (*opcional*) en donde podremos pasarle campos extras como el headers de la petición en caso de ser requerido

```ts
// Una petición post estandar solo lleva la url y el body
crearHeroe(heroe: HeoreModel): Observable<any> {
  return this.http.post(url, heroe)
}

// en caso de desear agregar un campo opcional quedaría
crearHeroe(heroe: HeoreModel): Observable<any> {
  let headers = new HttpHeaders().set('Content-Type','application/x-www-form-urlencoded');
  return this.http.post(url, heroe, {headers: headers})
}
```

#### PUT
El modo `PUT` reemplaza todas las representaciones actuales del recurso de destino con la carga útil de la petición.

#### DELETE
El método `DELETE` borra un recurso en específico.


## RxJS
La RxJS *(Reactive Extensions)* es una librería muy útil de Javascript, que te ayuda a gestionar flujos de datos asíncronos *(Programación Reactiva)*.
Como norma general, se usa el RxJS para todo código que tiene que gestionar más de un evento o requiere encadenar varias operaciones asíncronas. También es útil cuando se necesita gestionar de forma individual el éxito o error en la ejecución de varias operaciones asíncronas.
Los operadores de RxJs son funciones que pueden ser encadenadas en lo que llamamos la cadena o pipeline de operadores y que se sitúan entre medias del Observable y el Observer con el objetivo de filtrar, transformar o combinar los valores del Observable/Observables. 


#### Partes del RxJS
Se compone basicamente de los siguientes elementos:
*   **`Observable`:** El flujo de datos, una colección de eventos que se pueden emitir en algún momento.
*   **`Observer`:** Un objeto que escucha el flujo de datos y puede actuar sobre los valores que éste emite. En el patrón Observer, el Subject dispone de una API con 3 métodos principales:
    *  **[Suscribe](#suscribe)**: para que los Observers se suscriban
    *  **`Unsubscribe`**: para que los Observers cancelen la suscripción
    *  **`Notify`**: lo llama internamente cuando detecta cambios en su estado.
*   **`Subscription`:** Representa la ejecución de un observable y permite cancelarla.
*   **`Operador`:** Función para manipular los eventos siguiendo los principios de la programación funcional.
*   **`Subject`**: Similar al `Subject` del patrón Observer. En RxJS sirven para distribuir un Observable hacia varios Observers simultáneamente.
*   **`Schedulers`**: Los schedulers sirven para controlar el orden de las suscripciones y el orden y velocidad de emisión de eventos.

> Fuente de la información [acá](http://blog.enriqueoriol.com/2019/04/aprende-rxjs-3.html) y [acá](https://pablomagaz.com/blog/como-funcionan-operadores-rxjs)

#### Patrón Iterador
En este caso, se utiliza un objeto (el Iterador), como mecanismo para atravesar una colección de elementos (o contenedor) de forma secuencial, para acceder a su contenido.
La gracia del Patrón Iterador, es que te permite iterar la colección sin necesidad de conocer la estructura del contenedor, gracias a una API bien definida.

##### hasNext() & next()
La API de un Iterador, expone típicamente 2 métodos:

* **hasNext()** para saber si todavía quedan elementos en la colección (Booleano)
* **next()** para acceder al siguiente elemento de la colección


Por tanto te da igual como esté implementada la lista que contiene los datos, lo único que necesitas es saber que implementa el patrón iterador y que por tanto puedes usar estos dos métodos, 
```ts
let myArray = new IterableList ( 1, 2, 3, 4, 5 );
let iterator = myArray.iterator();

while( iterator.hasNext( ) ){
    console.log( iterator.next( ) );
}
//output: 1 2 3 4 5
```


#### Operadores RxJS
Un Operador es una función que crea un nuevo Observable basado en el Observable actual. Esta es una operación pura: el Observable anterior permanece sin modificar.
Esencialmente, un Operador es como una máquina que toma un Observable como entrada, realiza alguna lógica en los valores transmitidos a través del Observable y crea un nuevo Observable con estos valores, sin cambiar el Observable original.
<img src="img/OperatorExplanation.png" width="auto;"/>


##### of()
El Operador `of` es un Operador de creación. Los operadores de creación son funciones que crean un flujo observable a partir de una fuente.

El Operador `of` creará un Observable que emite una cantidad variable de valores en secuencia, seguido de una notificación de Finalización.
```ts
import { of } from 'rxjs';

const arr = [1, 2, 3];
const arr$ = of(arr);
arr$.subscribe((values) => console.log(`Emitted Values: `, values));
// Response: 
// Emitted Values: [1, 2, 3]
```
En este ejemplo al subscribirnos emitirá una única respuesta con el array completo, ya que el operador los toma como una única colección de datos, en caso de desear pasarlos por separados usando este operador debemos pasar los elementos dentro del `of` separados por comas
```ts
import { of } from 'rxjs';

const arr$ = of(1, 2, 3);
arr$.subscribe((values) => console.log(`Emitted Values: `, values));
// Response: 
// Emitted Values: 1
// Emitted Values: 2
// Emitted Values: 3
```
Si nos basamos en el primer ejemplo vemos  que `of` emitirá la matriz completa como un único valor. Esto contrasta con el operador `from`

##### from()
El Operador `from` convierte un Array, Promise o Iterable en un Observable.

Este operador convertirá una Promesa en un Observable, lo que permitirá que se maneje de una manera más reactiva. Cuando la Promesa se resuelva o rechace, se enviará una notificación de finalización a todos los suscriptores.

Además, a diferencia `of`, emitirá cada elemento en un Array o Iterable en secuencia, en lugar del valor completo. Una vez que se han emitido todos los elementos del Array o Iterable, se envía una notificación de finalización a los suscriptores.

```ts
import { from } from 'rxjs'; 

const arr = [1, 2, 3];
const arr$ = from(arr);
arr$.subscribe((values) => console.log(`Emitted Values: `, values));
// Response: 
// Emitted Values: 1
// Emitted Values: 2
// Emitted Values: 3
```
Como podemos el operador `form` tomó cada número y lo emitió como un valor. El suscriptor recibió cada valor en secuencia y llamó `console.log` tres veces.

También podemos usar un valor como una cadena:
```ts
import { from } from 'rxjs'; 

const fromString$ = from("Hello");
fromString$.subscribe((value) => console.log(`Emitted Values: `, value));
// Response: 
// Emitted Values: H
// Emitted Values: e
// Emitted Values: l
// Emitted Values: l
// Emitted Values: o
```

También podemos hacerlos con promesas, cuando la misma se resuelva el operador `form` podra ejecutarse
```ts
import { from } from 'rxjs'; 
const examplePromise = new Promise((resolve, reject) => {
  // Do some async code and resolve and object with an id property
  return resolve({ id: 1 });
});

const promise$ = from(examplePromise);
promise$.subscribe((value) => console.log(`Emitted Values: `, value));
```


##### Pipe()
El método `pipe()` permitirá ejecutar uno o varios operadores simultaneamente según tengamos la necesidad combinandolos y arrojando 1 solo resultado.
```ts
import { of } from 'rxjs';
import { filter, map } from 'rxjs/operators';

const obs = of({name: 'John Wayne', age: 72})
const mapped = obs.pipe(
                  filter(n => n.name== 'John Wayne'),
                  map(v => v.name));

mapped.subscribe(name => console.log (name));
```
Como se aprecia el método `pipe()` recibe un array de operadores, de modo que cada operador va modificando el flujo de datos.

##### Map()
El operador `Map` es llamado operador de transformación ya que nos permitirá manipular los datos recibidos y retornar un nuevo tipo de información más pulidad y precisa para la funcionalidad que estemos desarrollando sin tener que trabajar con el objeto entero.
```ts
import { of } from 'rxjs';
import { map } from 'rxjs/operators';

const obs = of({name: 'John Wayne', age: 72})
const mapped = obs.pipe(
                  map(v => v.name));

mapped.subscribe(name => console.log (name));
```
En este ejemplo el flujo de evento de la constante `obs` incluye un objeto con nombre y edad, como queremos obtener solo el nombre usamos el operador `map()`para retornar el dato a usar.
En caso que la petición a usar retorne algún tipo de error (un buen ejemplo al usar una petición de tipo `http`), provocará que el map no sea ejecutado.


#### Suscribe()
El método `suscribe()` es un método del tipo Observable el cual se ejecuta cuando se produce un evento indicado en el atributo subscrito. El tipo Observable es una utilidad que transmite datos de forma asíncrona o sincrónica a una variedad de componentes o servicios que se han suscrito al observable.  Su interfaz define 3 métodos (1 obligatorio y 2 opcionales):
*   **`next`:** *(Required)*. Método callback que recibe y usa los datos
*   **`error`:** *(Opcional)*. Método callback que escucha el flujo de datos y puede actuar sobre los valores que éste emite en caso de errores.
*   **`complete`:** *(Opcional)*. Método callback para la notificación de la ejecución completa.
```ts
myObservable.subscribe(
  x => console.log('Observer got a next value: ' + x),
  err => console.error('Observer got an error: ' + err),
  () => console.log('Observer got a complete notification')
);
```

#### Subjects
Los Subjects son Observables que además pueden manejar múltiples suscripciones a un único flujo y son capaces de emitir eventos.

Como los eventos solo los quieres generar a nivel interno, lo que debes hacer es crear un Subject privado, y exponer un Observable público con el flujo del primero.
#### Operadores RxJs vs Función de Orden Superior

Las funciones que operan en otras funciones, ya sea tomándolas como argumentos o retornandolas, se denominan `funciones de orden superior`, un buen ejemplo sería crear una función que permita sumar 2 números y retorne el resultado.
Si bien es buena idea ver los operadores de RxJs como algo parecido a las funciones de orden superior los operadores de RxJs trabajan de forma un poco diferente. La principal diferencia es que los Observables no generan estructuras de datos intermedias como si hacen las funciones de orden superior como `map` o `filter`
```ts
const data = [0,1,2,3];

const result = data
.filter(x => {
  console.log(`filter: ${x}`);
  return x % 2 === 0;
})
.map(x => {
  console.log(`map: ${x}`);
  return x * x;
})  
// OUTPUT >> filter: 0, filter: 1, filter: 2, filter: 3, map: 0, map: 2
```
Cada una de estas funciones siempre devuelve un nuevo Array, sin realizar mutaciones en el Array original y como vemos en la salida hasta que filter no devuelve un nuevo Array, éste, no pasa a la siguiente función que es map. En estructuras largas de datos, esto, tendrá un coste elevado por la duplicidad temporal de los datos. La misma operación en RxJs tiene un aspecto casi idéntico, pero funciona de forma diferente.
```ts
const data = [0,1,2,3];
const source$ = Rx.Observable.from(data);

source$
.filter(x => {
  console.log(`filter: ${x}`);
  return x % 2 === 0;
})
.map(x => {
  console.log(`map: ${x}`);
  return x * x;
})
.subscribe(); 
// OUTPUT >> filter: 0, map: 0, filter: 1, filter: 2, map: 2, filter: 3
```
Técnicamente, un operador, o al menos la gran mayoría de ellos, siempre devuelven un Observable, de tal forma que realmente cada operador actúa como subscriptor del Observable, usando para ello la API `next, complete y error` del Observer. En la salida podemos ver como cada uno de los valores emitidos va pasando por los distintos operadores sin formar estructuras de datos intermedias, lo que es mucho más rápido y eficiente.

## Storage
El objeto Storage (API de almacenamiento web) nos permite almacenar datos de manera local en el navegador y sin necesidad de realizar alguna conexión y/o consultas a una base de datos. 

#### Local Storage
Es una propiedades que accede al objeto Storage y tienen la función de almacenar datos de manera local, dicha información se almecena de forma indefinida o hasta que se decida limpiar los datos del navegador. Se almacenan de la manera llave-valor
```ts
// set a value
localStorage.setItem('Nombre', 'Miguel Antonio')
localStorage.Apellido = 'Márquez Montoya'

// get a value
localStorage.getItem('Nombre'),
localStorage.Apellido

// remove a single item
localStorage.removeItem('Nombre');
localStorage.removeItem(Apellido);

// clear the whole localStorage
localStorage.clear();
```

#### Session Storage
Es una propiedades que accede al objeto Storage y tienen la función de almacenar datos de manera local, dicha propiedad almacena la información mientras la pestaña donde se esté utilizando siga abierta, una vez cerrada, la información se elimina. Se almacenan de la manera llave-valor

```ts
// set a value
sessionStorage.setItem('Nombre', 'Miguel Antonio')
sessionStorage.Apellido = 'Márquez Montoya'

// get a value
sessionStorage.getItem('Nombre'),
sessionStorage.Apellido

// remove a single item
sessionStorage.removeItem('Nombre');
sessionStorage.removeItem(Apellido);

// clear the whole sessionStorage
sessionStorage.clear();
```

## Template Forms
Los formularios basados en plantillas como su propio nombre lo indica poseen la mayor parte de su lógica en el `HTML`, estos formularios se basan en directivas como `NgModel` y `NgModelGroup` la cuál crea un `FormGroup` y lo vincula a un formulario para realizar un seguimiento del valor agregado del formulario y el estado de validación.
Para poder hacer uso de este tipo de formularios se debe importar el `FormsModule` en el `app.module`, esto provocará que la directiva se active de forma predeterminada

```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { FormsModule } from '@angular/forms';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule,
    FormsModule],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
Los formularios basados en plantillas poseen distintas propiedades que se colocan en las diversas etiquetas 

* **`ngForm`**: Atributo base para formularios basados en template, se colocan en los `<form>` seguidos del nombre del formulario. Posee diversos eventos:
  * **`submitted: boolean`**: Devuelve si se ha activado el envío del formulario.
  * **`controls:[key:string]`**: Devuelve un mapa de los controles de este grupo.
* **`ngModel`**: Directiva que va acompañada de la propiedad `name` (propiedad por la cual sera nombrada la etiqueta) y generará ciertas propiedades que permitirán detectar varios eventos en las etiquetas donde este colocada. Posee diversos eventos:
  * **`pristine: boolean | null`**: Devuelve true si el valor inicial seteado al campo no ha sido modificado.
  * **`dirty: boolean | null`**: Devuelve true si el valor inicial seteado al campo ha sido modificado.
  * **`untouched: boolean | null`**: Devuelve true si el campo no ha sido tocado.
  * **`touched: boolean | null`**: Devuelve true si el campo ha sido tocado.
  * **`valid: boolean | null`**: Devuelve true si el campo ha pasado las validaciones.
  * **`invalid: boolean | null`**: Devuelve true si el campo no ha pasado las validaciones.

* **`ngSubmit`**: Evento base de la directiva que permite recibir la notificación cuando el usuario haya activado el envío de un formulario. La función a la que llaman suele recibir el formulario de tipo NgForm, esta propiedad se colocan en los `<form>`

```html
<form #forms="ngForm" (ngSubmit)="onSubmit(forms)" novalidate>
  <input name="first" ngModel required #first="ngModel">
  <input name="last" ngModel>
  <button>Submit</button>
</form>
```
```ts
onSubmit(forms){
  console.log(forms);
}
```
Para poder obtener la información del formulario debemos agregar la propiedad `ngForm`, para ello colocamos el nombre como desearemos llamar al formulario y lo igualamos a dicha propiedad. Las función que interactuará con el formulario al realizar un click, recibirá un atributo de tipo `NgForm`
```html
<form #forms="ngForm" (ngSubmit)="onSubmit(formu)" #formu="ngForm">
  <input name="first" ngModel required #first="ngModel">
  <input name="last" ngModel>
  <button>Submit</button>
</form>
```
```ts
onSubmit(formu:NgForm){
  console.log(forms);
}
```
En caso de desear colocar un valor predefinido a alguno de los parametros de nuestro formulario basta con igualar el `ngModel` al valor que vallamos a usar
```ts
usuario={
  nombre:'Luis',
  apellido:'Lopez'
}
```
```html
<form #forms="ngForm" (ngSubmit)="onSubmit(formu)" #formu="ngForm">
  <input name="first" [ngModel]="usuario.nombre" required #first="ngModel">
  <input name="last" ngModel>
  <button>Submit</button>
</form>
```
> El elemento se coloca entre `corchetes[]` para indicar que recibé un valor.

> El elemento se coloca entre `parentesis()` para indicar que emite un valor.

> El elemento se coloca entre `corchetes y parentesis[()]` para indicar que recibe y emite un valor. También se le conoce como la `caja de bananas`


#### Validaciones

* **Validators.required** = Comprueba que el campo sea llenado.
* **Validators.minLength** = Comprueba que el campo cumpla con un mínimo de caracteres.
* **Validators.maxLength** = Comprueba que el campo cumpla con un máximo de caracteres.
* **Validators.pattern** = Comprueba que el campo cumpla con un patrón usando una expresión regular.
* **Validators.email** = Comprueba que el campo cumpla con un patrón de correo válido.


## Reactive Forms
Los formularios reactivos son formularios dirigidos por modelos, es decir, emplean una técnica en la que los formularios se diseñan en el componente y luego se realizan los enlaces para el HTML. Para poder hacer uso de este tipo de formularios se debe importar el `ReactiveFormsModule` en el `app.module`.

```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { ReactiveFormsModule } from '@angular/forms';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule,
    ReactiveFormsModule],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

Los formularios reactivos se deben iniciarlizar en el componente antes que se empiece a crear el html, es por ello que es recomendable hacerlo en el `constructor` o en el `ngOnInit`.

Los formularios reactivos hacen uso de 3 principales clases `FormGroup` `FormControl` `FormBuilder`, un ejemplo sencillo de formulario reactivo sería

```html
<form novalidate (ngSubmit)="onSubmit()" [formGroup]="user">
  <label>
    <span>Username</span>
    <input
      type="text"
      placeholder="Your full name"
      formControlName="username">
  </label>
  <label>
      <span>Password</span>
      <input
        type="password"
        placeholder="Your passwornd"
        formControlName="password">
    </label>
  <button type="submit">Sign up</button>
</form>
```

```ts
import { Component, OnInit } from '@angular/core';
import { FormControl, FormGroup } from '@angular/forms';

@Component({...})
export class SignupFormComponent implements OnInit {
  user: FormGroup;
  ngOnInit() {
    this.user = new FormGroup({
      name: new FormControl(''),
      password: new FormControl(''),
      passwordRepeat: new FormControl('')
    });
  }
}
```

#### FormControl 
El FormControl es un objeto qué se usa en los formularios para tener un control sobre su valor y su estado en el formulario. Para registrar un control de formulario único, basta con importar la clase FormControl y crear una nueva instancia de FormControl para guardar como propiedad de clase.

```ts
import { Component } from '@angular/core';
import { FormControl } from '@angular/forms';

@Component({
  selector: 'app-name-editor',
  templateUrl: './name-editor.component.html',
  styleUrls: ['./name-editor.component.css']
})
export class NameEditorComponent {
  name = new FormControl('');
}
```
Se usa el constructor de `FormControl` para establecer su valor inicial, que en este caso es una cadena vacía. Al crear estos controles en el componente, el mismo obtiene acceso inmediato para escuchar, actualizar y validar el estado de la entrada del formulario.

Después de crear el control en la clase de componente, se debe asociar con un elemento de control de formulario en la plantilla.

```html
<label for="name">Name: </label>
<input id="name" type="text" [formControl]="name">
```
Usando la sintaxis de enlace de plantilla, el control de formulario ahora está registrado en el elemento de entrada de `name` en la plantilla. 

Los formularios reactivos tienen métodos para cambiar el valor de un control mediante el TS, lo que le brinda la flexibilidad de actualizar el valor sin la interacción del usuario. Una instancia de control de formulario puede ser `setValue()` que actualiza el valor del control en el formulario.
```ts
updateName() {
  this.name.setValue('Nancy');
}
```
```html
<button (click)="updateName()">Update Name</button>
```
<img src="img/fornControl.png" width="auto;"/>


#### FormGroup 
Un grupo de formularios o FormGroup es un objeto que define un formulario con un conjunto fijo de controles que puede administrar al mismo tiempo, el estado de este objeto depende del estado de todos sus objetos, es decir, si uno de los FormControl es inválido, el grupo entero es inválido. Para crear un grupo de formularios hay que seguir 3 pasos.

* Crear una instancia de FormGroup .
* Asociar el modelo y la vista de FormGroup .
* Guardar los datos del formulario.

Para crear una instancia de FormGroup debemos importar `FormGroup` y `FormControl`
```ts
import { Component } from '@angular/core';
import { FormGroup, FormControl } from '@angular/forms';

@Component({
  selector: 'app-profile-editor',
  templateUrl: './profile-editor.component.html',
  styleUrls: ['./profile-editor.component.css']
})
export class ProfileEditorComponent {
  profileForm = new FormGroup({
    firstName: new FormControl(''),
    lastName: new FormControl(''),
  });
}
```
Los `FormControl` ahora se recopilan dentro del `FormGroup`. Una instancia de `FormGroup` proporciona su valor de modelo como un objeto reducido de `FormControl`. Una instancia de `FormGroup` tiene las mismas propiedades (como `value` y `untouched` ) y métodos (como `setValue()`) como una de `FormControl`.

Para asociar el modelo a la vista basta con con agregar la propiedad al formulario de `[formGroup]="nombreDelFormEnElTs"` y agregar la entrada `formControlName` donde lo igualaremos a la key usada en nuestro formulario, para este ejemplo sería `firstName` y `lastName`
```html
<form [formGroup]="profileForm">

  <label for="first-name">First Name: </label>
  <input id="first-name" type="text" formControlName="firstName">

  <label for="last-name">Last Name: </label>
  <input id="last-name" type="text" formControlName="lastName">

</form>
```
Para guardar los datos del formulario debemos agregar el evento `ngSubmit` que escuchará el evento `submit` que generé el botón que procesará la data en el formulario y asignarle un método que recibirá las acciones a realizar

```html
<form [formGroup]="profileForm" (ngSubmit)="onSubmit()">
```

```ts
onSubmit() {
  // TODO: Usa EventEmitter con el valor del formulario
  console.log(this.profileForm.value);
}
```

A nivel del html el formulario final quedaría

```html
<form [formGroup]="profileForm" (ngSubmit)="onSubmit()">
  <label for="first-name">First Name: </label>
  <input id="first-name" type="text" formControlName="firstName">

  <label for="last-name">Last Name: </label>
  <input id="last-name" type="text" formControlName="lastName">

  <p>Complete the form to enable button.</p>
  <button type="submit" [disabled]="!profileForm.valid">Submit</button>
</form>
```
Para hacer referencia a cualquier de los `FormControl` internos de un `FormGroup` basta con usar la propiedad `get()` o `controls` dando como resultado
```ts
export class ProfileEditorComponent {
  profileForm = new FormGroup({
    firstName: new FormControl(''),
    lastName: new FormControl(''),
  });
  referencia(){
    // Opción con get
    this.profileForm.get('firstName').invalid
    // Opción con controls
    this.profileForm.controls['firstName'].invalid
    //Otra forma de opción con controls
    this.profileForm.controls.firstName.invalid
  }
}
```



##### FormGroup.get()
Recupera un control secundario dado el nombre o la ruta del control.
```ts
this.myForm.get('controlName')
```

##### FormGroup.setValue()
Establece el valor de `FormGroup`. Acepta un objeto que coincida con la estructura del grupo, con nombres de control como claves. En caso de faltar algún control por agregar mandará un error
```ts
this.form.setValue({
  nombre: "",
  apellido: "",
  correo: "",
  direccion: {
    distrito: "",
    ciudad: ""
  }
})
```

##### FormGroup.reset()
Restablece un `FormGroup` marcando a todos los descendientes como prístinos e intactos y establece el valor de todos los descendientes en nulo.

```ts
this.myForm.reset()
```

En caso de desear predefinir valores en el reset también podemos hacerlo generando una llave  similar a como se genera en el en la propiedad [setValue()](#setvalue) aunque se diferencia de este último método en que si falta algún valor del `FormGroup` por default lo reseteará en nulo.

```ts
this.form.reset({
  nombre: "Fernando",
  apellido: "Antúnez",
  correo: "fernan@gmail.com"
})
```

##### FormGroup.valueChanges
Un observable que emite un evento cada vez que cambia el valor del control. También emite un evento cada vez que llama a enable() o disabled().
```ts
// Puedes escuchar todos los campos a nivel general
this.form.valueChanges.subscribe(value => console.log(value))

// Puedes escuchar un campo en particular
this.form.get('usuario').valueChanges.subscribe(value => console.log(value))
```

##### FormGroup.statusChanges
Un observable que emite un evento indicando el `status` del formulario y/o campo, este estatus puede ser (valido/invalido).
```ts
// Puedes escuchar todos los campos a nivel general
this.form.statusChanges.subscribe(value => console.log(value))

// Puedes escuchar un campo en particular
this.form.get('usuario').statusChanges.subscribe(value => console.log(value))
```

#### FormBuilder 
Es un servicio del que han de depender los componentes que quieran desacoplar el modelo de la vista (Es decir formularios por template). Con el `FormBuilder` facilitaremos el andamiaje, especialmente cuando se construyen formularios complejos. 
Para usarlo debemos importarlo e inyectarlo desde el constructor

```ts
import { FormBuilder, FormGroup } from '@angular/forms';

export class ReactiveformsComponent {
  constructor(private formBuilder: FormBuilder){}
}
```

Usaremos el método `group()` disponible en `FormBuilder` para crear la instancia  `FormGroup` y luego agregar controles de formulario como un objeto. Los controles se agregarán similar a como se hacen en el `FormGroup` (Key-Value), aunque se diferenciará en que no necesitará instanciarlo

```ts
import { FormBuilder, FormGroup } from '@angular/forms';

export class ReactiveformsComponent {
  form: FormGroup;
 
  constructor(private formBuilder: FormBuilder){
    this.form = formBuilder.group({
      nombre: [''],
      apellido: [''],
      correo: ['']
    });
  }

  submit() {
    if (this.form.valid) {
      console.log(this.form.value)
    }
    else{
      alert("FILL ALL FIELDS")
    }
  }
}
}
```

A nivel del HTML se seguirá manteniendo la misma estructura que con el `FormGroup`, haciendo alusión a la misma variable

```html
<form autocomplete="off" [formGroup]="form" (ngSubmit)="submit()">
  <div>
    <div class="form-group row">
      <label class="col-2 col-form-label">Nombre</label>
      <div class="col-8">
        <input class="form-control" type="text" placeholder="Nombre" formControlName="nombre">
      </div>
    </div>

    <div class="form-group row">
      <label class="col-2 col-form-label">Apellido</label>
      <div class="col-8">
        <input class="form-control" type="text" placeholder="Apellido" formControlName="apellido">
      </div>
    </div>
  </div>

  <div class="form-group row">
    <label class="col-2 col-form-label">Correo</label>
    <div class="col-8">
      <input class="form-control" type="email" placeholder="Correo electrónico" formControlName="correo">
    </div>
  </div>

  <div class="form-group row">
    <label class="col-2 col-form-label">&nbsp;</label>
    <div class="input-group col-md-8">
      <button type="submit" class="btn btn-outline-primary btn-block">
        Guardar
      </button>
    </div>
  </div>
</form>
```

#### Nested Forms
Los `FormGroup` pueden aceptar internamente tanto instancias de `FormControl` como otras instancias de `FormGroup` hijos. A esto se le conoce como formularios anidados. Para hacer un formulario anidado se debe con
Crear un grupo anidado desde el TS.
Agrupa el formulario anidado en la plantilla (HTML) utilizando la directiva `formGroupName`.

```ts
import { Component } from '@angular/core';
import { FormGroup, FormControl } from '@angular/forms';

export class ProfileEditorComponent {
  profileForm = new FormGroup({
    firstName: new FormControl(''),
    lastName: new FormControl(''),
    address: new FormGroup({
      street: new FormControl(''),
      city: new FormControl(''),
      state: new FormControl(''),
      zip: new FormControl('')
    })
  });
}
```

En este ejemplo, el `FormGroup` hijo `address`, se combina con los `FormControl` `firstName` y `lastName`. Esto también es replicable cuando usamos  `FormBuilder` de la siguiente manera

```ts
import { Component } from '@angular/core';
import { FormBuilder } from '@angular/forms';

export class ProfileEditorComponent {
  profileForm = this.fb.group({
    firstName: [''],
    lastName: [''],
    address: this.fb.group({
      street: [''],
      city: [''],
      state: [''],
      zip: ['']
    }),
  });

  constructor(private fb: FormBuilder) { }
}
```
A nivel de la plantilla debemos agregar el nuevo `FormGroup` usando la directiva `formGroupName` e igualandolo al nombre del elemento de tipo `FormGroup`.Los `FormControl` hijos automáticamente se relacionarán según el `formGroupName` que los antecedan.

```html
<div formGroupName="address">
  <h2>Address</h2>

  <label for="street">Street: </label>
  <input id="street" type="text" formControlName="street">

  <label for="city">City: </label>
  <input id="city" type="text" formControlName="city">

  <label for="state">State: </label>
  <input id="state" type="text" formControlName="state">

  <label for="zip">Zip Code: </label>
  <input id="zip" type="text" formControlName="zip">
</div>
```

Para hacer referencia a cualquier de los `FormControl` internos de un `FormGroup` hijo basta con usar la propiedad `get()` o `controls` dando como resultado
```ts
export class ProfileEditorComponent {
  profileForm = new FormGroup({
    firstName: new FormControl(''),
    lastName: new FormControl(''),
  });
}

export class ProfileEditorComponent {
  profileForm = this.fb.group({
    firstName: [''],
    lastName: [''],
    address: this.fb.group({
      street: [''],
      city: [''],
      state: [''],
      zip: ['']
    }),
  });

  constructor(private fb: FormBuilder) { }

  referencia(){
    // Opción con get
    this.profileForm.get('address.street').invalid
    // Opción con get
    this.profileForm.get('address').get('street').invalid
    //Otra forma de opción con controls
    this.profileForm.controls.address.get('street').invalid
  }
}

```

#### FormArray
Los `FormArray` son una alternativa a FormGroup para administrar cualquier número de controles sin nombre. Al igual que con las instancias de grupos de formularios, puede insertar y eliminar controles. Sin embargo, no necesita definir una clave para cada control por nombre, por lo que esta es una gran opción si no se conoce la cantidad de valores secundarios de antemano.

Para definir un formulario dinámico con `FormArray` se debe.

* Importar la clase FormArray.
* Defina un control FormArray .
* Acceda al control FormArray con un método getter.
* Mostrar la matriz del formulario en una plantilla.

Importar la clase `FormArray` de `@angular/forms` para usarse dentro de un elemento de tipo `FormGroup`. 
```ts
import { FormArray } from '@angular/forms';
```
En caso de estar utilizando el servicio `FormBuilder` ya este provee el método `FormBuilder.array()` para definir la matriz y el método `FormBuilder.control()` para llenar la matriz con un control inicial.
```ts
profileForm = this.fb.group({
  firstName: ['', Validators.required],
  lastName: [''],
  address: this.fb.group({
    street: [''],
    city: [''],
    state: [''],
    zip: ['']
  }),
  aliases: this.fb.array([
    this.fb.control('')
  ])
});
```
Para acceder al control de tipo `FormArray` desde el HTML es recomendable definir un getter que retorne una instancia del elemento de tipo `FormArray`.
```ts
get aliases() {
  return this.profileForm.get('aliases') as FormArray;
}
```
> **Nota**: Debido a que el control devuelto es del tipo AbstractControl , debe proporcionar un tipo explícito (en este caso `FormArray`) para acceder a la sintaxis del método para la instancia de matriz de formulario (es decir desde el HTML).


Para agregar nuevos elementos en nuestro `FormArray` es tan sencillo como usar un método `push()` el cual inserte un elemento de tipo `FormControl`, en este caso lo usamos a través del servicio `FormBuilder`

```ts
addAlias() {
  this.aliases.push(this.fb.control(''));
}
```
Para conectar el `FormArray` del componente con la plantilla HTML ocurre de forma similar que con el `formGroupName`, acá usaremos la propiedad `formArrayName` que vinculará entre el TS y el HTML .

```html
<div formArrayName="aliases">
  <h2>Aliases</h2>
  <button (click)="addAlias()" type="button">+ Add another alias</button>

  <div *ngFor="let alias of aliases.controls; let i=index">
    <! - La plantilla de alias repetida ->
    <label for="alias-{{ i }}">Alias:</label>
    <input id="alias-{{ i }}" type="text" [formControlName]="i">
  </div>
</div>
```
En vista que los nuevos `FormControl` no poseén nombres definidos, se le asignarán de manera dinámica a través del indice.

En caso que deseemos cargar data de manera predefinida al formulario se deberá hacer usando la propiedad [FormGroup.setValue()](#formgroupsetvalue) o pusheando item por item a través de un forEach
```ts
['comer','dormir'].forEach(value => this.myFormArray.push(this.formBuilder.control(value)))
```

##### FormArray.push()
Inserta un nuevo `FormControl` al final de la matriz.
```ts
this.myFormArray.push(this.fb.control(''));
```

##### FormArray.removeAt()
Elimina el `FormControl` en el índice dado en la matriz.
```ts
this.myFormArray.removeAt(index);
```

#### Validators
Los Validators en los formularios reactivos son el proceso de revisión que verifica la correcta inserción de datos en los campos que los componente, por lo general se solían realizar agregando atributos HTML tales como el `required`. Pero todo eso ahora se realizan desde el TS, donde se podra establecer una o varias reglas de validación.
Para su uso debemos importarlo de `@angular/forms`
```ts
import { FormBuilder, FormGroup, Validators } from '@angular/forms';
```
Para utilizarse desde el TS nos dirigimos al campo donde haremos su llamado y las agregaremos después del valor
```ts
'field': [_value_, [validaciones_sincrónicas], [validaciones_asíncronas]]
```
Existirán 2 tipos de validaciones sincrónicas y asíncronas

##### Validaciones sincrónicas
Las validaciones sincrónicas son aquellas en las que no necesitamos de consultar ninguna fuente externa para comprobar los datos, como por ejemplo validar que el email tiene el formato correcto, validar que el usuario sea un adulto a partir de la edad, validar un número mínimo de caracteres etc. Entre los Validators sincrónicas más usados tendríamos.

* **Validators.required** = Comprueba que el campo sea llenado. Uso `Validators.required`
* **Validators.minLength** = Comprueba que el campo cumpla con un mínimo de caracteres. Uso `Validators.minLength(5)`
* **Validators.maxLength** = Comprueba que el campo cumpla con un máximo de caracteres. Uso `Validators.maxLength(10)`
* **Validators.pattern** = Comprueba que el campo cumpla con un patrón usando una expresión regular. Uso `Validators.pattern('regular_expression')`
* **Validators.email** = Comprueba que el campo cumpla con un patrón de correo válido. Uso `Validators.email` (_no se recomienda_)

```ts
this.form = this.formBuilder.group({
  nombre: ['', [Validators.required, Validators.minLength(5)]],
  apellido: ['', [Validators.required, Validators.maxLength(20)]],
  correo: ['', [Validators.pattern('[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,3}$')]]
})
```
De manera sincrónica también podemos crear validaciones personalizadas, para ello debemos dirigirnos a donde instanciamos nuestro formulario y agregar el campo `options?` de la método `group` donde podremos agregar nuestra nueva validación, Este tipo de validaciones debén retornar un `ValidationErrors` (un objeto con un nombre que querramos y un booleano) o un `null` en caso de no existir error
```ts
this.form = this.fb.group(
  {
    password: ["", Validators.required],
    confirmarPassword: ["", Validators.required],
  },
  {
    validators: passwordIguales('password', 'confirmarPassword'),
  }
)
```

```ts
passwordIguales(pass1Name: string, pass2Name: string): ValidationErrors | null {
  return (formGroup: FormGroup) => {
    const pass1Control = formGroup.controls[pass1Name]
    const pass2Control = formGroup.controls[pass2Name]
    if (pass1Control === pass2Control) {
      pass2Control.setErrors(null);
    } else {
      pass2Control.setErrors({ noEsIgual: true });
    }
  }
}
```

##### Validaciones asíncronas
Las validaciones asíncronas son aquellas en las cuales debemos hacer una solicitud externa y de acuerdo a ello validar los datos, estas solicitudes suelen devolver un `Promise` o un `Observable`, un buen ejemplo para validaciones asíncronas es cuando insertamos un nombre de usuario (username), primero debemos hacer una solicitud a nuestra base de datos y comprobar que el nombre de usuario está disponible.
Las validaciones asíncronas se colocan en el tercer campo
```ts
crearForm() {
  this.form = this.formBuilder.group({
    usuario: ['', Validators.required, this.validadoresService.existeUsuario]
  });
}
```
> **NOTA:** En caso no requerir alguna validación sincrona podemos dejar el espacio en blanco `usuario: ['', , this.validadoresService.existeUsuario]`

```ts
existeUsuario(control:FormControl): Promise<any> | Observable<any> {
  return new Promise((res, err) =>{
    setTimeout(() => {

      if (control.value === "fercho") {
        res({existe:true});
      } else {
        res(null);
      }
    }, 3000);
  });
}
```

## Bootstrap
Existen varias manera de instalar bootstrap en nuestro proyecto, si nuestro proyecto usa internet se recomienda el uso del CDN de bootstrap, a nivel local existen otras maneras como el uso de paquetes de node. Para ello basta con instalar el bootstrap, jquery y popper
```sh
npm install bootstrap --save
npm install jquery@1.9.1 popper.js@^1.16.1 --save
```
Luego nos dirigimos al archivo `angular.json` en la sección de build/styles y build/scripts los paquetes de arranque 
```json
"build": {
  "styles": [
    "src/styles.css",
    "node_modules/bootstrap/dist/css/bootstrap.min.css"
  ],
  "scripts": [
    "node_modules/jquery/jquery.min.js",
    "node_modules/popper.js/dist/umd/popper.min.js",
    "node_modules/bootstrap/dist/js/bootstrap.min.js"
  ]
},
```
> La desventaja de tenerlo de forma local es que estas librerías pasan a ser parte del `bundle` provocando que el programa final pese un poco más.

## Angular Material
Angular Material es un módulo construido para Angular que permite implementar componentes con un diseño basado en Material Design.

#### Instalación y Configuración
Para la instalación desde el CLI de angular basta con agregar el siguiente comando:
```sh
ng add @angular/material
```
Esto agregará las dependencias al package, instalará la fuente roboto y fuentes del icono de Material Design en el `index.html` y agregará estilos globales en el archivo `style.css`

#### MatButton
Es un componente UI de Angular Material que renderiza `<button>` e hipervínculos `<a>`. Se importa con el módulo `MatButtonModule` en nuestro módulo a trabajar

```ts
import {MatButtonModule} from '@angular/material/button';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule,BrowserAnimationsModule,MatButtonModule],
  providers: [],
  bootstrap: [AppComponent]
})
```
Para usarlos basta con colocar alguno de los atributos en nuestra etiqueta

* **mat-button** = Botón de texto rectangular sin elevación
* **mat-raised-button** = Botón rectangular contenido con elevación
* **mat-flat-button** = Botón contenido rectangular sin elevación
* **mat-stroked-button** = Botón rectangular con contorno sin elevación
* **mat-icon-button** = Botón circular con fondo transparente, destinado a contener un icono
* **mat-fab** = Botón circular con elevación, predeterminado al color de acento del tema.
* **mat-mini-fab** = Igual que mat-fabpero más pequeño

```html
<button mat-raised-button>
  Click
</button>
```
Los botones podrán ser coloreados en función al tema que se este utilizando usado la propiedad `color` para establecer el forndo `primary`, `accent` o `warn`.
```html
<button mat-raised-button color="primary">
  Click
</button>
```