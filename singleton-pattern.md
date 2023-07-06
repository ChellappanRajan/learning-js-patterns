# Singleton Pattern
The Singleton pattern ensures that only one instance of a class is created and accessed globally. It is great for sharing global state across an application.

Example in JavaScript:

```javascript
class SingletonTheme {
    static instance;
    #theme = 'light';

    constructor() {
        if (!SingletonTheme.instance) {
            SingletonTheme.instance = SingletonTheme.instance ?? this;
        }
        return SingletonTheme.instance;
    }

    toggleTheme() {
        this.#theme = this.#theme === 'light' ? 'dark' : 'light';
    }

    get theme() {
        return this.#theme;
    }
}

const theme1 = new SingletonTheme();
theme1.toggleTheme();

const theme2 = new SingletonTheme();

console.log(theme1.theme, theme2.theme);
```

In this code, the `SingletonTheme` class has a static property that holds the singleton instance of the class. The constructor checks whether an instance already exists. If it does, it returns that instance.


Example using Angular:

In Angular, singleton classes can be created using the following example:

**theme.service.ts:**

```typescript
@Injectable({
    providedIn: 'root'
})
class SingletonTheme {
    #theme = 'light';

    toggleTheme() {
        this.#theme = this.#theme === 'light' ? 'dark' : 'light';
    }

    get theme() {
        return this.#theme;
    }
}
```

**theme.component.ts:**

```typescript
@Component({
    ...
})
class ThemeComponent {
    themeService = Inject(SingletonTheme);

    constructor() {
        this.themeService.theme;
    }
}
```
