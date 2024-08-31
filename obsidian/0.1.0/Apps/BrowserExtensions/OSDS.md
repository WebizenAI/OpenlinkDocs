## The OpenLink Structured Data Sniffer (OSDS)

## What is the OpenLink Structured Data Sniffer?

The OpenLink Structured Data Sniffer (OSDS) is a browser extension for [Google Chrome](http://www.google.com/chrome), [Microsoft Edge](https://www.microsoft.com/en-us/windows/microsoft-edge), [Mozilla Firefox](http://www.mozilla.org/firefox), [Opera](http://www.opera.com/), and [Vivaldi](https://vivaldi.com/) (with a build planned for [Apple Safari](http://www.apple.com/safari/)) that unveils structured metadata embedded within HTML documents and web pages.

## Why is the OpenLink Structured Data Sniffer Important?

At its core, every search engine optimization (SEO) effort requires agility in managing document metadata.

OSDS benefits include:

- **Productive Search Engine Optimization** — All the major search engines are moving towards modern algorithms based on semantically-rich metadata embedded in Web Pages.
- **GPS-like navigation of the Web** — In addition to basic link-traversal, new ![24px OSDS Query icon](https://osds.openlinksw.com/images/osds-icon-query-24.png) **Query** and ![24px OSDS Describe icon](https://osds.openlinksw.com/images/osds-icon-describe-24.png) **Describe** buttons provide powerful tools for intelligently navigating the Web with lots of serendipitous discoveries along the way (just follow-your-nose by clicking!)
- **Read-Write operations on the Web** — Rather than being confined to basic tagging and bookmarking, the new ![24px OSDS Annotate icon](https://osds.openlinksw.com/images/osds-icon-annotate-24.png) **Annotate** button places you in a browser hosted editor that makes note taking about documents of interest trivial.
- **Local & Cloud Storage** — Rather than being confined to cloud storage provided by 3rd parties, the ![24px OSDS Download icon](https://osds.openlinksw.com/images/osds-icon-download-24.png) **Download** button lets you save extracted metadata or new annotations to cloud or local storage.

Key new features in v2.14.x include:

- **Improved sniffing** — OSDS now handles RDF/XML and JSON-LD.
- **Improved sniffing** — Any notation supported as nanotation within an HTML document is now also supported if contained in a properly MIME-typed standalone documents.
- **Support for Microsoft Edge** — through a downloadable ZIP for manual installation. Availability through the Microsoft Store is pending.
- **Web Services Console** — decomposes URIs of pages you visit, allowing better understanding, easy alteration, and resubmission of those URIs.
- **Distinguishing Browser (User Agent) Identity from User Identity** — identify _you_ distinctly from _the Web Browser that you are using_ when presenting data requests to HTTP services. This allows you to take advantage of open standards like URIs, URLs, HTTP, X.509 Certificates, PKI, and TLS.

Key new features in v2.9.0 included:

- **new Plain Semantic Old HTML (POSH) tab** — exposes Metadata embedded in HTML docs using `<meta />` and `<link />` notations.
- **Support for Twitter Card metadata** — as part of POSH extractions.

Key new features in v2.6.1 included:

- **Nanotation sniffing** — OSDS is now able to sniff out RDF-Turtle (or RDF-Ntriples) statements embedded in the body of HTML documents and/or text pages.
- **Improved default SPARQL query** — Clicking on the ![24px OSDS Query icon](https://osds.openlinksw.com/images/osds-icon-query-24.png) **Query** button returns a page that has been automatically enhanced (via Natural Language Processing, Machine Learning, and Entity Extraction) for immediate Linked Data exploration.
- **Sniffed content download** — Extracted data can be saved to to Turtle or JSON-LD documents on any filesystem-accessible location, including folders mounted from the likes of Dropbox, Google Drive, OneDrive, etc.

## How do I use the OpenLink Structured Data Sniffer?

### Download and Installation

Installation is a few simple steps, which vary with your browser.

#### Google Chrome

There are two options for basic installation of OSDS —

- You may choose to install [the latest stable OSDS release available in the Chrome Store](https://chrome.google.com/webstore/detail/openlink-structured-data/egdaiaihbdoiibopledjahjaihbmjhdj), as with any other Chrome add-on.
    
- If you prefer, you may install the latest development version, which takes a few more steps, as follow --
    
    1. Download the `zip` or `tar.gz` source code archive from the [OSDS Github page](https://github.com/openlink/structured-data-sniffer/releases/latest).
    2. Extract the archive to a local directory/folder.
    3. Open the **Chrome** browser.
    4. Select from menu: **Chrome** -> **Preferences** -> **Extensions**.
    5. Check the **Developer mode** box.
    6. Choose the option **Load Unpacked Extension...**
    7. Navigate to the folder containing the extracted source code.
    8. Press the **Select** button.
    9. OSDS will be added to your browser's installed extensions list.

This brief (less than 2 minutes) video shows the whole Chrome process, including a live test of functionality.

##### Optimizing Interaction in Chrome

After basic installation, a few browser UI/UX tweaks may be required to enable optimal use of OSDS.

1. Open a new browser window or tab.
2. Locate the OSDS icon ![16px OSDS icon](https://osds.openlinksw.com/images/osds-icon-16.png) in the toolbar. Depending on how many other extensions you have installed, the size of your browser window, and other variables, it may have "overflowed" to the Chrome menu ![Chrome menu icon](https://osds.openlinksw.com/images/chrome-menu-icon.png).
    
    [![osds-chrome1-extension-menu](https://osds.openlinksw.com/images/osds-chrome1-extension-menu.400.png)](https://osds.openlinksw.com/images/osds-chrome1-extension-menu.png)
    
3. If the OSDS icon has overflowed, right- or control-click it, and choose **Keep in Toolbar**.
    
    [![osds-chrome2-keep-in-toolbar](https://osds.openlinksw.com/images/osds-chrome2-keep-in-toolbar.400.png)](https://osds.openlinksw.com/images/osds-chrome2-keep-in-toolbar.png)
    
4. Click-and-drag the OSDS icon to the immediate right of the Omnibox (where the current page's URL is displayed) or wherever you prefer.
    
     [![osds-chrome3-toolbar-cust](https://osds.openlinksw.com/images/osds-chrome3-toolbar-cust.400.png)](https://osds.openlinksw.com/images/osds-chrome3-toolbar-cust.png)  →   [![osds-chrome4-ready](https://osds.openlinksw.com/images/osds-chrome4-ready.400.png)](https://osds.openlinksw.com/images/osds-chrome4-ready.png)
    

#### Microsoft Edge (Windows 10 Anniversary Update or later)

Our installation guide for Edge was based on [this general user's guide](https://www.howtogeek.com/249921/how-to-install-extensions-in-microsoft-edge/) and [this developer's guide](https://github.com/MicrosoftDocs/edge-developer/blob/develop/microsoft-edge/extensions/guides/adding-and-removing-extensions.md), each of which may have other information that is helpful to you.

Eventually, you'll be able to get OSDS from the Windows Store. For now,

1. Download the `[OSDS_Edge_2_14_1.zip](http://osds.openlinksw.com/downloads/OSDS_Edge_2_14_1.zip)` file to a local directory/folder, and unzip its content to a directory of your choosing.
2. Open the **Edge** browser.
3. If this is the first extension you're manually installing
    1. type '**`about:flags`**' into the address bar.
    2. Select the **Enable extension developer features** checkbox.
    3. Select **More (...)** to open the menu.
4. If you've manually installed one or more extensions in the past, click or tap the menu button in the top-right corner of the window, and select "**Extensions**." (If you don’t see an Extensions option in the list here, you need to upgrade to the [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/windows/features).)
5. The Extensions panel will appear, listing all your installed extensions.
6. Select Extensions from the menu.
7. Select the Load extension button.
8. Navigate to the folder you extracted to in step 1 (or the folder within) that contains the `manifest.json` file and click the **Select folder** button.  
    _**NOTE:** If you encounter an error message when loading the extension, refer to the troubleshooting page for guidance._
9. You should now see OSDS listed in Microsoft Edge's extension pane.

_**NOTE:** For the time being, Microsoft Edge will ask if you want to enable this extension every time the browser is restarted. Once OSDS is approved for and installed from the Microsoft Store, this prompt will stop repeating._

This brief (less than a minute) video shows the whole Edge process, including a live test of functionality.

#### Mozilla Firefox (v28+)

There are two options for basic installation of OSDS —

- You may choose to install [the latest stable OSDS release available in the Mozilla Extensions Store](https://addons.mozilla.org/en-US/firefox/addon/openlink-structured-data-sniff/), as with any other Firefox add-on.
    
- If you prefer, you may install the latest development version (note that this archive may _pre- or post-date_ the stable release above), which takes a few more steps, as follow --
    
    1. Download the `[openlink_structured_data_sniffer-2.18.0-fx.xpi](http://osds.openlinksw.com/downloads/openlink_structured_data_sniffer-2.18.0-fx.xpi)` file to a local directory/folder, and unzip its content.
    2. Open the **Firefox** browser (v28 or later).
    3. In address bar type: **`about:config`**.
    4. Click the **I'll be careful, I promise** button.
    5. Search for **`xpinstall.signatures.required`**.
    6. Double click that line, repeating if necessary until the value is set to **false**.
    7. In address bar type: **`about:addons`**.
    8. Click on the Gear icon and select **Install Add-On from file...** from the menu.
    9. Navigate to the **`openlink_structured_data_sniffer-2.9.0-fx.xpi`** file you downloaded. Select this file, and click the **Open** button.
    10. Click the **Install** button.
    11. OSDS will be added to your browser's installed extensions list.

This brief (less than 2 minutes) video shows the whole Firefox process, including a live test of functionality.

##### Optimizing Interaction in Firefox

After basic installation, a few browser UI/UX tweaks may be required to enable optimal use of OSDS.

1. Open a new browser window or tab.
2. Locate the OSDS icon ![16px OSDS icon](https://osds.openlinksw.com/images/osds-icon-16.png) in the toolbar. Depending on how many other extensions you have installed, the size of your browser window, and other variables, it may have "overflowed" to the extension menu **»**.
    
    [![osds-ff0-ext-menu-overflow](https://osds.openlinksw.com/images/osds-ff0-ext-menu-overflow.400.png)](https://osds.openlinksw.com/images/osds-ff0-ext-menu-overflow.png)
    
3. If it's in the overflow, right-click it and select "Move to Menu". (This is necessary because Customization doesn't allow items to be dragged directly from the overflow.)
    
    [![osds-ff1-ext-overflow](https://osds.openlinksw.com/images/osds-ff1-ext-overflow.400.png)](https://osds.openlinksw.com/images/osds-ff1-ext-overflow.png)
    
4. Click the menu icon ![Chrome menu icon](https://osds.openlinksw.com/images/chrome-menu-icon.png) and enter Toolbar customization mode by clicking **Customize**.
    
    [![osds-ff2-ext-menu-cust](https://osds.openlinksw.com/images/osds-ff2-ext-menu-cust.400.png)](https://osds.openlinksw.com/images/osds-ff2-ext-menu-cust.png)
    
5. Click-and-drag the OSDS icon from the menu listing to the immediate right of the address box (where the current page's URL is displayed) or wherever you prefer.
    
     [![osds-ff3-ext-menu-cust](https://osds.openlinksw.com/images/osds-ff3-ext-menu-cust.400.png)](https://osds.openlinksw.com/images/osds-ff3-ext-menu-cust.png)  →   [![osds-ff4-ext-menu-cust](https://osds.openlinksw.com/images/osds-ff4-ext-menu-cust.400.png)](https://osds.openlinksw.com/images/osds-ff3-ext-menu-cust.png)
    
6. Click **Exit Customize**, and OSDS is ready for efficient use.
    
    [![osds-ff5-ready](https://osds.openlinksw.com/images/osds-ff5-ready.400.png)](https://osds.openlinksw.com/images/osds-ff5-ready.png)
    

#### Opera

1. Download the `zip` or `tar.gz` source code archive from the [OSDS Github page](https://github.com/openlink/structured-data-sniffer/releases/latest).
2. Extract the archive to a local directory/folder.
3. Open the **Opera** browser.
4. In the address bar, type **`opera://extensions`**.
5. Click the **Developer Mode** button.
6. Choose the option **Load unpacked extension...**.
7. Navigate to the folder containing the extracted source.
8. Click the **Select** button.
9. OSDS will be added to your browser's installed extensions list.

#### Vivaldi

1. Download the `zip` or `tar.gz` source code archive from the [OSDS Github page](https://github.com/openlink/structured-data-sniffer/releases/latest).
2. Extract the archive to a local directory/folder.
3. Open the **Vivaldi** browser.
4. In the address bar, type **`vivaldi://extensions`**.
5. Click the **Developer Mode** button.
6. Choose the option **Load unpacked extension...**.
7. Navigate to the folder containing the extracted source, and to the **`src`** folder therein.
8. Click the **Select** button.
9. OSDS will be added to your browser's installed extensions list.