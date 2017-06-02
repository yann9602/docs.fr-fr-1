---
title: "Comment&#160;: cr&#233;er un service WCF compatible AJAX et un client ASP.NET qui acc&#232;de &#224; ce service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er un service WCF compatible AJAX et un client ASP.NET qui acc&#232;de &#224; ce service
Cette rubrique indique comment utiliser Visual Studio 2008 pour créer un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] compatible AJAX et un client ASP.NET qui accède au service. Le code pour le service et pour le client est fourni dans la section Exemple après les étapes de création décrites dans la section Procédures.  
  
### <a name="to-create-the-aspnet-client-application"></a>Pour créer l'application cliente ASP.NET  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  À partir de la **fichier** menu, sélectionnez **nouveau**, puis **projet**, puis **Web**, puis sélectionnez **Application Web ASP.NET**.  
  
3.  Nommez le projet `SandwichServices` sur **OK**.  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a>Pour créer le service WCF compatible AJAX  
  
1.  Avec le bouton droit le `SandwichServices` de projet dans le **l’Explorateur de solutions** et sélectionnez **ajouter**, puis **un nouvel élément**, puis **Service WCF compatible AJAX**.  
  
2.  Nommez le service `CostService` dans les **nom** , puis cliquez sur **ajouter**.  
  
3.  Ouvrez le fichier CostService.svc.cs.  
  
4.  Spécifier la `Namespace` de <xref:System.ServiceModel.ServiceContractAttribute> comme `SandwichService`:  
  
    ```  
    namespace SandwichServices  
    {  
      [ServiceContract(Namespace = "SandwichServices")]  
      [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
       public class CostService  
       {  
         …  
       }  
     }  
    ```  
  
5.  Implémentez les opérations dans le service. Ajouter la <xref:System.ServiceModel.OperationContractAttribute> à chacune des opérations pour indiquer qu’ils font partie du contrat. L'exemple suivant implémente une méthode qui retourne le coût d'une quantité donnée de sandwichs.  
  
    ```  
    public class CostService  
    {  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
    // Add more operations here and mark them with [OperationContract]  
    }  
    ```  
  
### <a name="to-configure-the-client-to-access-the-service"></a>Pour configurer le client pour accéder au service  
  
1.  Ouvrez la page Default.aspx et sélectionnez le **conception** vue.  
  
2.  À partir de la **affichage** menu, sélectionnez **boîte à outils**.  
  
3.  Développez le **Extensions AJAX** nœud et glisser-déplacer un **ScriptManager** sur la page Default.aspx.  
  
4.  Cliquez sur le **ScriptManager** et sélectionnez **propriétés**.  
  
5.  Développez le **Services** collection dans le **propriétés** fenêtre à ouvrir le **éditeur de collections ServiceReference** fenêtre.  
  
6.  Cliquez sur **ajouter**, spécifiez `CostService.svc` comme le **chemin d’accès** référencé, puis cliquez sur **OK**.  
  
7.  Développez le **HTML** nœud dans le **boîte à outils** et faites glisser une **entrée (bouton)** sur la page Default.aspx.  
  
8.  Cliquez sur le **bouton** et sélectionnez **propriétés**.  
  
9. Modifier la **valeur** champ `Price for 3 Sandwiches`.  
  
10. Double-cliquez sur le **bouton** pour accéder au code JavaScript.  
  
11. Passez dans le code JavaScript suivant dans la `script`> élément.  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a>Pour accéder au service depuis le client  
  
1.  Utilisez Ctrl + F5 pour lancer le service et le client Web. Cliquez sur le **prix de 3 Sandwiches grillé** bouton pour générer la sortie attendue de « 3,75 ».  
  
## <a name="example"></a>Exemple  
 Cet exemple contient le code de service contenu dans le fichier WCFService.svc.cs et le code client contenu dans le fichier Default.aspx.  
  
```  
//The service code contained in the CostService.svc.cs file.  
  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace SandwichServices  
{  
    [ServiceContract(Namespace="SandwichServices")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class CostService  
    {  
        // Add [WebGet] attribute to use HTTP GET  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
        // Add more operations here and mark them with [OperationContract]  
    }  
}  
//The code for hosting the service is contained in the CostService.svc file.  
  
<%@ ServiceHost Language="C#" Debug="true" Service="SandwichServices.CostService" CodeBehind="CostService.svc.cs" %>  
  
//The client code contained in the Default.aspx file.  
  
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="SandwichServices._Default" %>  
  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
  
<html >  
<head runat="server">  
    <title>Untitled Page</title>  
<script language="javascript" type="text/javascript">  
// <!CDATA[  
  
function Button1_onclick() {  
var service = new SandwichServices.CostService();  
service.CostOfSandwiches(3, onSuccess, null, null);  
}  
  
function onSuccess(result){  
alert(result);  
}  
  
// ]]>  
</script>  
</head>  
<body>  
    <form id="form1" runat="server">  
    <div>  
  
    </div>  
    <asp:ScriptManager ID="ScriptManager1" runat="server">  
        <services>  
            <asp:servicereference Path="CostService.svc" />  
        </services>  
    </asp:ScriptManager>  
    </form>  
    <p>  
        <input id="Button1" type="button" value="Price for 3 Sandwiches" onclick="return Button1_onclick()" /></p>  
</body>  
</html>  
  
```  
  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->