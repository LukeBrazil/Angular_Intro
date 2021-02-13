# Introduction to Angular

This project was authored by Luke Brazil.

## What is does:

A simple app that uses the `Angular Http Method` to search for brewies and display the results.


## Code Snippets:

1) Fetch Brewery Data

```
import { Component, OnInit } from '@angular/core';
import { HttpService } from '../http.service'

@Component({
  selector: 'app-list',
  templateUrl: './list.component.html',
  styleUrls: ['./list.component.scss']
})
export class ListComponent implements OnInit {

  brews: Array<any> = [];

  constructor(private fetch: HttpService) { 
  }

  ngOnInit(): void {
    this.fetch.getBeer().subscribe(data => {
      this.brews = data as Array<Object>;
      console.log(this.brews)
    })
  }

}

2) Display brewery data

```
<h1>Breweries</h1>

<ul *ngIf='brews'>
    <li *ngFor='let brew of brews'>
        <p class='name'>{{ brew.name }}</p>
        <p class='country'>{{ brew.country }}</p>
        <a href='{{ brew.website_url }}' class='site' target='_blank'>Site</a>
    </li>
</ul>

```



