# CORS

#### **Disable CORS for working on a microservice API with localhost**

*   Disable CORS for development by importing "cors" and then use it to disable cors for 'development' in each microservice

    `if (process.env.NODE_ENV === 'development') { log.info('disable cors'); app.use(cors()); }`

    EXAMPLE w/ cors: [https://github.com/Greenstand/treetracker-stakeholder-api/blob/main/server/app.js](https://github.com/Greenstand/treetracker-stakeholder-api/blob/main/server/app.js)

    EXAMPLE w/ header options: [https://github.com/Greenstand/treetracker-web-map-api/blob/master/src/app.js](https://github.com/Greenstand/treetracker-web-map-api/blob/master/src/app.js)
* Chrome extension that will let you disable CORS when you want without having to shutdown&#x20;
  * Simple option:  [**Cross Domain CORS**](https://chrome.google.com/webstore/detail/cross-domain-cors/mjhpgnbimicffchbodmgfnemoghjakai?hl=en-US) or [**Moesif CORS**](https://chrome.google.com/webstore/detail/moesif-origin-cors-change/digfbfaphojjndkpccljibejjbppifbc?hl=en-US) **-** You can click the red button to make it active when you want to disable CORS. &#x20;
  * Lots of settings, but you have to create an account: [**Requestly**](https://chrome.google.com/webstore/detail/requestly-modify-headers/mdnleldcmiljblolnjhpnblkcekpdkpa)
* Try different browsers or the proxy setting for CRA.\
  [https://medium.com/swlh/avoiding-cors-errors-on-localhost-in-2020-5a656ed8cefa](https://medium.com/swlh/avoiding-cors-errors-on-localhost-in-2020-5a656ed8cefa)
* Create your own proxy server: [https://medium.com/nodejsmadeeasy/a-simple-cors-proxy-for-javascript-applications-9b36a8d39c51](https://medium.com/nodejsmadeeasy/a-simple-cors-proxy-for-javascript-applications-9b36a8d39c51)



#### **Helpful reading!**

Debugging: [https://httptoolkit.tech/blog/how-to-debug-cors-errors/](https://httptoolkit.tech/blog/how-to-debug-cors-errors/)\
Explain settings: [https://web.dev/cross-origin-resource-sharing/](https://web.dev/cross-origin-resource-sharing/)\
CORS module settings: [https://expressjs.com/en/resources/middleware/cors.html](https://expressjs.com/en/resources/middleware/cors.html)
