---



copyright:

  years: 2017

lastupdated: "2017-06-22"


---

{:codeblock: .codeblock}
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# {{site.data.keyword.registrylong_notm}}CLI
{: #containerregcli}

La CLI {{site.data.keyword.registrylong}} è un plug-in per la gestione del tuo registro e delle relative risorse per il tuo account.
{: shortdesc}

**Prerequisiti**
* Prima di eseguire i comandi del registro, accedi a {{site.data.keyword.Bluemix_short}}
 con il comando `bx login` per generare un token di accesso {{site.data.keyword.Bluemix_short}}
 e autenticare la tua sessione.

Per scoprire come utilizzare la CLI {{site.data.keyword.registrylong}}, vedi [Impostazione di un registro delle immagini privato](../../../services/Registry/index.html).

<table summary="Gestione del tuo registro dei contenitori">
<caption>Tabella 1. Comandi per la gestione di {{site.data.keyword.registryshort}} su {{site.data.keyword.Bluemix_short}}
</caption>
 <thead>
 <th colspan="5">Comandi per la gestione del registro</th>
 </thead>
 <tbody>
 <tr>
 <td>[bx cr api](#bx_cr_api)</td>
 <td>[bx cr info](#bx_cr_info)</td>
 <td>[bx cr image-inspect](#bx_cr_image_inspect)</td>
 <td>[bx cr image-list (bx cr images)](#bx_cr_image_list)</td>
 <td>[bx cr image-rm](#bx_cr_image_rm)</td>
 </tr>
 <tr>
 <td>[bx cr login](#bx_cr_login)</td>
 <td>[bx cr namespace-add](#bx_cr_namespace_add)</td>
 <td>[bx cr namespace-list (bx cr namespaces)](#bx_cr_namespace_list)</td>
 <td>[bx cr namespace-rm](#bx_cr_namespace_rm)</td>
 <td>[bx cr plan](#bx_cr_plan)</td>
 </tr>
 <tr>
 <td>[bx cr plan-upgrade](#bx_cr_plan_upgrade)</td>
 <td>[bx cr pricing](#bx_cr_pricing)</td>
 <td>[bx cr quota](#bx_cr_quota)</td>
 <td>[bx cr quota-set](#bx_cr_quota_set)</td>
 <td>[bx cr token-add](#bx_cr_token_add)</td>
 </tr>
 <tr>
 <td>[bx cr token-get](#bx_cr_token_get)</td>
 <td>[bx cr token-list (bx cr tokens)](#bx_cr_token_list)</td>
 <td>[bx cr token-rm](#bx_cr_token_rm)</td>
 <td>[bx cr vulnerability-assessment (bx cr va)](#bx_cr_va)</td>
 </tr>
 </tbody></table>



## bx cr api
{: #bx_cr_api}

Restituisce i dettagli sull'endpoint dell'API del registro per cui vengono eseguiti i comandi.

```
bx cr api
```
{: codeblock}


## bx cr info
{: #bx_cr_info}

Visualizza il nome e l'account del registro a cui sei collegato.

```
bx cr info
```
{: codeblock}


## bx cr image-inspect
{: #bx_cr_image_inspect}

Visualizza i dettagli di una specifica immagine.

```
bx cr image-inspect [--format FORMAT] IMAGE [IMAGE...]
```
{: codeblock}

**Parametri**

<dl>
<dt>--format FORMAT</dt>
<dd>(Facoltativo) Formatta gli elementi di output utilizzando un modello Go. 

Per ulteriori informazioni, vedi [Visualizzazione di informazioni sulle immagini](../../../services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
<dt>IMAGE</dt>
<dd>Il percorso di registro {{site.data.keyword.Bluemix_short}} completo dell'immagine che desideri analizzare, in formato `namespace/image:tag`. Se nel percorso dell'immagine non è specificata alcuna tag, viene analizzata l'immagine contrassegnata con `latest`. Puoi analizzare più immagini elencando ogni percorso del registro {{site.data.keyword.Bluemix_short}} privato nel comando con uno spazio tra ogni percorso.</dd>
</dl>


## bx cr image-list (bx cr images)
{: #bx_cr_image_list}

Visualizza tutte le immagini nel tuo account {{site.data.keyword.Bluemix_short}}.

```
 bx cr image-list [--no-trunc] [-q, --quiet] [--include-ibm] [--format FORMAT]
```
{: codeblock}

**Parametri**
<dl>
<dt>--no-trunc</dt>
<dd>(Facoltativo) Non troncare i digest immagine.</dd>
<dt>-q, --quiet</dt>
<dd>(Facoltativo) Ogni immagine viene elencata nel formato: `repository:tag`.</dd>
<dt>--include-ibm</dt>
<dd>(Facoltativo) Include le immagini pubbliche fornite da IBM nell'output. Senza questa opzione, vengono elencate solo le immagini private per impostazione predefinita.</dd>
<dt>--format FORMAT</dt>
<dd>(Facoltativo) Formatta gli elementi di output utilizzando un modello Go. 

Per ulteriori informazioni, vedi [Visualizzazione di informazioni sulle immagini](../../../services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
</dl>


## bx cr image-rm
{: #bx_cr_image_rm}

Elimina una o più immagini specificate dal tuo registro.

```
bx cr image-rm IMAGE [IMAGE...]
```
{: codeblock}

**Parametri**
<dl>
<dt>IMAGE</dt>
<dd>Il percorso di registro {{site.data.keyword.Bluemix_short}} completo dell'immagine che desideri rimuovere , in formato `namespace/image:tag`. Se nel percorso dell'immagine non è specificata alcuna tag, per impostazione predefinita verrà eliminata l'immagine con tag `latest`. Puoi rimuovere più immagini elencando ogni percorso del registro {{site.data.keyword.Bluemix_short}} privato nel comando con uno spazio tra ogni percorso.</dd>
</dl>


## bx cr login
{: #bx_cr_login}

Questo comando esegue il comando `docker login` sul registro. Il comando `docker login` è obbligatorio per abilitare l'esecuzione dei comandi `docker push` o `docker pull` per il registro. Questo comando non è obbligatorio per eseguire altri comandi `bx cr`. Se Docker non è installato, questo comando restituisce un messaggio di errore.

```
bx cr login
```
{: codeblock}


## bx cr namespace-add
{: #bx_cr_namespace_add}

Aggiunge uno spazio dei nomi al tuo account {{site.data.keyword.Bluemix_short}}.

```
bx cr namespace-add NAMESPACE
```
{: codeblock}

**Parametri**
<dl>
<dt>NAMESPACE</dt>
<dd>Lo spazio dei nomi che desideri aggiungere. Lo spazio dei nomi deve essere univoco tra tutti gli account {{site.data.keyword.Bluemix_short}} nella stessa regione.</dd>
</dl>


## bx cr namespace-list (bx cr namespaces)
{: #bx_cr_namespace_list}

Visualizza tutti gli spazi dei nomi che appartengono al tuo account {{site.data.keyword.Bluemix_short}}.

```
bx cr namespace-list
```
{: codeblock}


## bx cr namespace-rm
{: #bx_cr_namespace_rm}

Rimuove uno spazio dei nomi dal tuo account {{site.data.keyword.Bluemix_short}}. Le immagini in questo spazio dei nomi vengono eliminate quando si rimuove lo spazio dei nomi.

```
bx cr namespace-rm NAMESPACE
```
{: codeblock}

**Parametri**
<dl>
<dt>NAMESPACE</dt>
<dd>Lo spazio dei nomi che desideri rimuovere.</dd>
</dl>



## bx cr plan
{: #bx_cr_plan}

Visualizza il piano dei prezzi.

```
bx cr plan
```
{: codeblock}


## bx cr plan-upgrade
{: #bx_cr_plan_upgrade}

Esegue il tuo upgrade al piano specificato.

Per informazioni sui piani, vedi [Piani del registro](../../../services/Registry/registry_overview.html#registry_plans).

```
bx cr plan-upgrade PLAN
```
{: codeblock}

**Parametri**
<dl>
<dt>PIANO</dt>
<dd> Esegue il tuo upgrade al piano specificato. Sono disponibili i seguenti piani: 
<ul>
<li>Gratuito</li>
<li>Standard</li>
</ul>
</dl>


## bx cr pricing
{: #bx_cr_pricing}

Calcola il costo stimato del tuo utilizzo in dollari americani, tenendo conto delle tue franchigie per l'archiviazione e il traffico di pull.

```
bx cr pricing --traffic VALUE --storage VALUE
```
{: codeblock}

**Parametri**
<dl>
<dt>--traffic VALUE</dt>
<dd>Specifica il traffico di pull mensile previsto in megabyte. Il traffico deve essere specificato come numero intero.</dd>
<dt>--storage VALUE</dt>
<dd>Specifica l'archiviazione media totale prevista in megabyte. L'archiviazione deve essere specificata come numero intero.</dd>
</dl>


## bx cr quota
{: #bx_cr_quota}

Visualizza le tue quote correnti per traffico e archiviazione e le informazioni di utilizzo rispetto a tali quote.

```
bx cr quota
```
{: codeblock}


## bx cr quota-set
{: #bx_cr_quota_set}

Modifica la quota specificata.

```
bx cr quota-set [--traffic VALUE] [--storage VALUE]
```
{: codeblock}

**Parametri**
<dl>
<dt>--traffic VALUE</dt>
<dd>(Facoltativo) Modifica la tua quota di traffico al valore specificato. L'operazione non riesce se non sei autorizzato a impostare il traffico o se imposti un valore che supera il tuo piano dei prezzi corrente.</dd>
<dt>--storage VALUE</dt>
<dd>(Facoltativo) Modifica la tua quota di archiviazione al valore specificato. L'operazione non riesce se non sei autorizzato a impostare le quote di archiviazione o se imposti un valore che supera il tuo piano dei prezzi corrente.</dd>
</dl>


## bx cr token-add
{: #bx_cr_token_add}

Aggiunge un token che puoi utilizzare per controllare l'accesso a un registro.

```
bx cr token-add [--description VALUE] [-q, --quiet] [--non-expiring] [--readwrite]
```

{: codeblock}


**Parametri**
<dl>
<dt>--description VALUE</dt>
<dd>(Facoltativo) Specifica il valore come descrizione per il token, che viene visualizzata quando esegui `bx cr token-list`. Se il tuo token viene creato automaticamente dal servizio IBM Bluemix Container, la descrizione viene impostata sul nome del tuo cluster Kubernetes. In questo caso, il token viene rimosso automaticamente alla rimozione del cluster.</dd>
<dt>-q, --quiet</dt>
<dd>(Facoltativo) Visualizza solo il token, senza alcun testo circostante.</dd>
<dt>--non-expiring</dt>
<dd>(Facoltativo) Crea un token con l'accesso che non scade. Se questo parametro non è impostato, l'accesso da un token scade dopo 24 ore per impostazione predefinita.</dd>
<dt>--readwrite</dt>
<dd>(Facoltativo) Crea un token che concede l'accesso di lettura e scrittura. Senza questa opzione, l'accesso è di sola lettura per impostazione predefinita.</dd>
</dl>


## bx cr token-get
{: #bx_cr_token_get}

Richiama il token specificato dal registro.

```
bx cr token-get TOKEN
```

{: codeblock}

**Parametri**
<dl>
<dt>TOKEN</dt>
<dd>(Facoltativo) L'identificativo univoco del token che desideri richiamare.</dd>
</dl>


## bx cr token-list (bx cr tokens)
{: #bx_cr_token_list}

Visualizza tutti i token esistenti per il tuo account {{site.data.keyword.Bluemix_short}}.

```
bx cr token-list --format FORMAT
```
{: codeblock}

**Parametri**
<dl>
<dt>--format FORMAT</dt>
<dd>(Facoltativo) Formatta gli elementi di output utilizzando un modello Go. 

Per ulteriori informazioni, vedi [Visualizzazione di informazioni sulle immagini](../../../services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
</dl>

## bx cr token-rm
{: #bx_cr_token_rm}

Rimuove uno o più token specificati.

```
bx cr token-rm TOKEN [TOKEN...]
```
{: codeblock}

**Parametri**
<dl>
<dt>TOKEN</dt>
<dd>(Facoltativo) TOKEN può essere il token stesso o l'identificativo univoco del token, come mostrato in `bx cr token-list`. È possibile specificare più token e devono essere separati da uno spazio.</dd>
</dl>


## bx cr vulnerability-assessment (bx cr va)
{: #bx_cr_va}

Visualizza un report di valutazione delle vulnerabilità per un'immagine.

```
bx cr vulnerability-assessment IMAGE [IMAGE...]
```
{: codeblock}

**Parametri**
<dl>
<dt>IMAGE</dt>
<dd>Il percorso di registro {{site.data.keyword.Bluemix_short}} completo, nel formato `spaziodeinomi/immagine:tag`, all'immagine per cui vuoi ottenere un report. Il report ti informa se l'immagine ha delle vulnerabilità di pacchetto note. Sono supportati i seguenti sistemi operativi:

<ul>

<li>Alpine</li>
<li>CentOS</li>
<li>Debian</li>
<li>RHEL (Red Hat Enterprise Linux)</li>
<li>Ubuntu</li>
</ul>

Per ulteriori informazioni, vedi [Riesame della sicurezza delle immagini](../../../services/Registry/registry_images_.html#registry_security_checking).

</dd>

</dl>

