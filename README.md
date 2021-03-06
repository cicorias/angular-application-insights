# MS Azure Application Insights Angular v2+ implementation

> Connect your Angular 2+ client-side to Microsofts Application Insights with this easy-to-use Module. 

## Installation:

Install & save the library to your package.json:

Latest version: **2.3.0**

> Updated to Angular 4.0 (use npm version 1.x for Angular 2.x)

--- 

```bash
$ npm i -S @markpieszak/ng-application-insights
```

and then add the library to your Angular Root `AppModule`:

```typescript
// Import the Application Insights module and the service provider
import { ApplicationInsightsModule, AppInsightsService } from '@markpieszak/ng-application-insights';

@NgModule({
  imports: [
    // ... your imports

    // Add the Module to your imports 
    ApplicationInsightsModule.forRoot({
      instrumentationKey: 'Your-Application-Insights-instrumentationKey'
    })
  ],
  // ... providers / etc
  providers: [ ..., AppInsightsService ],
})
export class YourRootModule { }
```

## Usage:

Through out your application you can now use the AppInsightsService class to fire off AppInsights functionality.

```typescript
import { AppInsightsService } from '@markpieszak/ng-application-insights';

export class ShoppingCartComponent {
  public cart: [];
  constructor(private appInsightsService: AppInsightsService) {}

  saveCart(user) {
    // MOCK Example of sending a trackEvent()
    // Saving some sample user & cart product data
    this.appInsightsService.trackEvent('ShoppingCart Saved', { 'user': user.id, 'cart': cart.id });
  }
}
```

## API:

You can see a list of the API here: https://github.com/Microsoft/ApplicationInsights-JS/blob/master/API-reference.md#class-appinsights

```typescript
AppInsightsService.trackEvent()
AppInsightsService.startTrackEvent()
AppInsightsService.stopTrackEvent()
AppInsightsService.trackPageView()
AppInsightsService.startTrackPage()
AppInsightsService.stopTrackPage()
AppInsightsService.trackMetric()
AppInsightsService.trackException()
AppInsightsService.trackTrace()
AppInsightsService.trackDependency()
AppInsightsService.flush()
AppInsightsService.setAuthenticatedUserContext()
AppInsightsService.clearAuthenticatedUserContext()
```

## If using SystemJS:

Modify systemjs.config.js...

In System.Config.map, add:

```typescript
      'applicationinsights-js': 'npm:applicationinsights-js/JavaScript/JavaScriptSDK.Module/AppInsightsModule.js',
      '@markpieszak/ng-application-insights': 'npm:@markpieszak/ng-application-insights/dist/index.js'
```

and in System.Config.packages, add:

```typescript
      '.': {
         defaultExtension: 'js'
      }
```

---

# Want to Contribute?

## ng-Application-Insights Development

To generate all `*.js`, `*.js.map` and `*.d.ts` files:

```bash
$ npm run build
```

To lint all `*.ts` files:

```bash
$ npm run lint
```

## License

MIT © [Mark Pieszak](mailto:mpieszak84@gmail.com)
