---
title: "Comment&#160;: migrer des services Web ASP.NET compatibles AJAX vers WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# Comment&#160;: migrer des services Web ASP.NET compatibles AJAX vers WCF
Cette rubrique décrit les procédures de migration d'un service de base ASP.NET AJAX vers un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] compatible AJAX équivalent.  Elle indique comment créer une version [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] d'un service ASP.NET AJAX équivalente en termes de fonctionnalités.  Vous pouvez soit utiliser les deux services côte à côte, soit utiliser le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour remplacer le service ASP.NET AJAX.  
  
 La migration d'un service ASP.NET AJAX existant vers un service AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] offre les avantages suivants :  
  
-   Vous pouvez exposer votre service AJAX en tant que service SOAP avec une configuration supplémentaire minimale.  
  
-   Vous pouvez profiter des fonctions de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] telles que le suivi.  
  
 Les procédures suivantes partent du principe que vous utilisez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
 Le code qui résulte de l'exécution des procédures mentionnées dans cette rubrique est fourni dans l'exemple qui suit les procédures.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'exposition d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] par le biais d'un point de terminaison compatible AJAX, consultez la rubrique [Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### Pour créer et tester l'application de service Web ASP.NET  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Dans le menu **Fichier**, sélectionnez **Nouveau**, **Projet**, **Web**, puis cliquez sur **Application de service Web ASP.NET**.  
  
3.  Nommez le projet `ASPHello` et cliquez sur **OK**.  
  
4.  Supprimez les marques de commentaire dans la ligne du fichier Service1.asmx.cs qui contient `System.Web.Script.Services.ScriptService]` pour rendre ce service compatible avec AJAX.  
  
5.  Dans le menu **Générer**, sélectionnez **Générer la solution**.  
  
6.  Dans le menu **Déboguer**, sélectionnez **Exécuter sans débogage**.  
  
7.  Sur la page Web générée, sélectionnez l'opération `HelloWorld`.  
  
8.  Cliquez sur le bouton **Appeler** dans la page de test `HelloWorld`.  Vous recevez alors la réponse XML suivante.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. Cette réponse confirme que vous bénéficiez désormais d'un service ASP.NET AJAX fonctionnel et, plus précisément, que le service a exposé un point de terminaison à Service1.asmx\/HelloWorld qui répond aux requêtes HTTP POST et retourne du code XML.  
  
     Vous êtes maintenant prêt à convertir ce service pour utiliser un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX.  
  
### Pour créer une application de service AJAX WCF équivalente  
  
1.  Cliquez avec le bouton droit sur le projet **ASPHello** et sélectionnez **Ajouter**, **Nouvel élément**, puis **Service WCF compatible AJAX**.  
  
2.  Nommez le service `WCFHello` et cliquez sur **Ajouter**.  
  
3.  Ouvrez le fichier WCFHello.svc.cs.  
  
4.  À partir de Service1.asmx.cs, copiez l'implémentation suivante de l'opération `HelloWorld`.  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  Collez l'implémentation copiée de l'opération `HelloWorld` dans le fichier WCFHello.svc.cs à la place du code suivant.  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  Spécifiez l'attribut `Namespace` de <xref:System.ServiceModel.ServiceContractAttribute> sous la forme `WCFHello`.  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  Ajoutez <xref:System.ServiceModel.Web.WebInvokeAttribute> à l'opération `HelloWorld` et définissez la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> de sorte qu'elle retourne <xref:System.ServiceModel.Web.WebMessageFormat>.  Notez que si la propriété n'est pas définie, le type de retour par défaut est <xref:System.ServiceModel.Web.WebMessageFormat>.  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  Dans le menu **Générer**, sélectionnez **Générer la solution**.  
  
9. Ouvrez le fichier WCFHello.svc, puis dans le menu **Déboguer**, sélectionnez **Exécuter sans débogage**.  
  
10. Le service expose désormais un point de terminaison à `WCFHello.svc/HelloWorld`, qui répond aux requêtes HTTP POST.  Les requêtes HTTP POST ne peuvent pas être testées à partir du navigateur, mais le point de terminaison retourne le code XML suivant.  
  
    ```  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. Les points de terminaison `WCFHello.svc/HelloWorld` et `Service1.aspx/HelloWorld` sont désormais équivalents d'un point de vue fonctionnel.  
  
## Exemple  
 Le code qui résulte de l'exécution des procédures mentionnées dans cette rubrique est fourni dans l'exemple suivant.  
  
```  
//This is the ASP.NET code in the Service1.asmx.cs file.  
  
using System;  
using System.Collections;  
using System.ComponentModel;  
using System.Data;  
using System.Linq;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Linq;  
using System.Web.Script.Services;  
  
namespace ASPHello  
{  
    /// <summary>  
    /// Summary description for Service1.  
    /// </summary>  
    [WebService(Namespace = "http://tempuri.org/")]  
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
    [ToolboxItem(false)]  
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.   
    [System.Web.Script.Services.ScriptService]  
    public class Service1 : System.Web.Services.WebService  
    {  
  
        [WebMethod]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
    }  
}   
  
//This is the WCF code in the WCFHello.svc.cs file.  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace ASPHello  
{  
    [ServiceContract(Namespace = "WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class WCFHello  
    {  
        // Add [WebInvoke] attribute to use HTTP GET.  
        [OperationContract]  
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
  
        // Add more operations here and mark them with [OperationContract].  
    }  
}  
```  
  
 Le type <xref:System.Xml.XmlDocument> n'est pas pris en charge par <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> car il n'est pas sérialisable par <xref:System.Xml.Serialization.XmlSerializer>.  Vous pouvez utiliser un type <xref:System.Xml.Linq.XDocument> ou sérialiser <xref:System.Xml.XmlDocument.DocumentElement%2A> à la place.  
  
 Si les services Web ASMX font l'objet d'une mise à niveau et d'une migration côte à côte avec les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], évitez de mapper deux types au même nom sur le client.  Cela provoque une exception dans les sérialiseurs si le même type est utilisé dans un <xref:System.Web.Services.WebMethodAttribute> et un <xref:System.ServiceModel.ServiceContractAttribute> :  
  
-   Si le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est ajouté en premier, l'appel de la méthode sur le service Web ASMX provoque une exception dans <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> parce que la définition du style [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de l'ordre dans le proxy est prioritaire.  
  
-   Si le service Web ASMX est ajouté en premier, l'appel de la méthode sur le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provoque une exception dans <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> parce que la définition de style de service Web de l'ordre dans le proxy est prioritaire.  
  
 Il existe des différences de comportement importantes entre le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et le <xref:System.Web.Script.Serialization.JavascriptSerializer> ASP.NET AJAX.  Par exemple, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> représente un dictionnaire sous la forme d'un tableau de paires clé\/valeur, alors que <xref:System.Web.Script.Serialization.JavascriptSerializer> ASP.NET AJAX représente un dictionnaire sous la forme d'objets JSON réels.  Par conséquent, le code suivant est le dictionnaire représenté dans ASP.NET AJAX.  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add(“one”, 1);  
d.Add(“two”, 2);  
```  
  
 Ce dictionnaire est représenté dans des objets JSON comme indiqué dans la liste suivante :  
  
-   \[{"Key":"one","Value":1},{"Key":"two","Value":2}\] par <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
  
-   {“one”:1,”two”:2} par <xref:System.Web.Script.Serialization.JavascriptSerializer> ASP.NET AJAX  
  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est plus puissant car il peut gérer des dictionnaires où le type de clé n'est pas une chaîne, alors que <xref:System.Web.Script.Serialization.JavascriptSerializer> ne le peut pas.  Cependant, ce dernier est plus compatible avec JSON.  
  
 Les différences principales entre ces sérialiseurs sont résumées dans le tableau suivant.  
  
|Catégorie de différences|DataContractJsonSerializer|JavaScriptSerializer ASP.NET AJAX|  
|------------------------------|--------------------------------|---------------------------------------|  
|Désérialisation de la mémoire tampon vide \(nouvel octet \[0\]\) dans <xref:System.Object> \(ou <xref:System.Uri> ou d'autres classes\).|SerializationException|null|  
|Sérialisation de <xref:System.DBNull.Value>|{} \(ou {"\_\_type":"\#System"}\)|Null|  
|Sérialisation des membres privés de types \[Sérialisable\].|sérialisé|n'est pas sérialisé|  
|Sérialisation des propriétés publiques de types <xref:System.Runtime.Serialization.ISerializable>.|n'est pas sérialisé|sérialisé|  
|« Extensions » de JSON|Respecte la spécification JSON, qui exige des guillemets sur les noms de membres d'objet \({"a":"hello"}\).|Prend en charge les noms de membres d'objet sans guillemets \({a:"hello"}\).|  
|<xref:System.DateTime> temps universel \(UTC, Universal Time Coordinated\)|Ne prend pas en charge le format « \\\/Date\(123456789U\)\\\/ » ou « \\\/Date\\\(\\d\+\(U&#124;\(\\\+\\\-\[\\d{4}\]\)\)? »  \\\)\\\\\/\)".|Prend en charge les formats "\\\/Date\(123456789U\)\\\/" et "\\\/Date\\\(\\d\+\(U&#124;\(\\\+\\\-\[\\d{4}\]\)\)?  \\\)\\\\\/\) » comme valeurs DateTime.|  
|Représentation de dictionnaires|Un tableau de KeyValuePair\<K,V,\>gère des types de clé qui ne sont pas des chaînes.|Comme objets JSON réels \- mais gère uniquement des types de clé qui sont des chaînes.|  
|Caractères d'échappement|Toujours avec une barre oblique d'échappement \(\/\) ; n'autorise jamais de caractères JSON non valides sans séquence d'échappement, tels que "\\n".|Avec une barre oblique d'échappement \(\/\) pour les valeurs DateTime.|  
  
## Voir aussi  
 [Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)