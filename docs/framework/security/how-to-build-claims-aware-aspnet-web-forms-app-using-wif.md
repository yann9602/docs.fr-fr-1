---
title: "Comment&#160;: g&#233;n&#233;rer une application Web Forms ASP.NET prenant en charge les revendications &#224; l’aide de WIF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# Comment&#160;: g&#233;n&#233;rer une application Web Forms ASP.NET prenant en charge les revendications &#224; l’aide de WIF
## S'applique à  
  
-   Foundation \(WIF\) d'identité Microsoft® Windows®  
  
-   ASP.NET® Web Forms  
  
## Résumé  
 Cet " Comment " fournit des procédures pas \- à \- pas détaillées pour créer l'application prenant en charge les revendications simple Web Forms ASP.NET.  Il fournit également des instructions sur la façon de teste la requête prenant en charge les revendications simple Web Forms ASP.NET d'implémentation réussie de l'authentification fédérée.  Cet " Comment " n'a pas le obtenir des instructions détaillées pour créer un service d'émission de jeton de sécurité \(STS\), et le suppose que vous avez déjà configuré STS.  
  
## Sommaire  
  
-   Objectifs  
  
-   Résumé des étapes  
  
-   Étape 1 \- créez une simple application Web Forms ASP.NET  
  
-   Étape 2 \- configurer l'application Web Forms ASP.NET d'authentification Basée Revendication\-  
  
-   Étape 3 \(testez votre solution  
  
## Objectifs  
  
-   Configurez la demande Web Forms ASP.NET d'authentification basée revendication\-  
  
-   Testez l'application prenant en charge les revendications réussie Web Forms ASP.NET  
  
## Résumé des étapes  
  
-   Étape 1 \- créez l'application ASP.NET simple Web Forms  
  
-   Étape 2 \- configurer l'application Web Forms ASP.NET d'authentification fédérée  
  
-   Étape 3 \(testez votre solution  
  
## Étape 1 \- créez une simple application Web Forms ASP.NET  
 Dans cette étape, vous allez créer une application Web Forms ASP.NET.  
  
#### Pour créer une simple application ASP.NET  
  
1.  Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2.  Dans la fenêtre de **Nouveau projet** , cliquez sur **Application Web Forms ASP.NET**.  
  
3.  Dans **Nom**, entrez `TestApp` et appuyez **OK**.  
  
## Étape 2 \- configurer l'application Web Forms ASP.NET d'authentification Basée Revendication\-  
 Dans cette étape vous ajouterez des entrées de configuration *dans le fichier de configuration Web.config* de votre application Web Forms ASP.NET de le informer.  
  
#### Pour configurer l'application ASP.NET d'authentification basée revendication\-  
  
1.  Ajoutez les entrées suivantes de section de configuration *dans le fichier de configuration Web.config* immédiatement après l' **\<configuration\>** élément d'ouverture :  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  Ajoutez un élément de **\<location\>** qui permet d'accéder aux métadonnées de fédération de l'application :  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3.  Ajoutez les entrées de configuration suivantes dans les éléments de **\<system.web\>** pour refuser des utilisateurs, désactivez l'authentification native, et permettent à WIF de gérer l'authentification.  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  Ajoutez un élément de **\<system.webServer\>** qui définit les packages pour l'authentification fédérée.  Notez que l'attribut *de PublicKeyToken* doit être le même que l'attribut *de PublicKeyToken* pour les entrées de **\<configSections\>** a ajouté précédemment :  
  
    ```  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  Ajoutez les entrées de configuration connexes par Windows Foundation IDENTITY suivantes et vérifiez l'URL de cette votre application ASP.NET et la correspondance de numéro de port les valeurs dans l'entrée de **\<audienceUris\>** , l'attribut de **domaine** de l'élément de **\<wsFederation\>** , et l'attribut de **réponse** de l'élément de **\<wsFederation\>** .  Assurez\-vous également que la valeur **expéditeur** ajuste votre URL de \(STS\) de service d'émission de jeton de sécurité.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6.  Ajoutez la référence à l'assembly d' [System.IdentityModel](assetId:///System.IdentityModel?qualifyHint=False&amp;autoUpgrade=True) .  
  
7.  Compilez la solution pour vous assurer qu'il existe des erreurs.  
  
## Étape 3 \(testez votre solution  
 Dans cette étape vous allez tester votre application Web Forms ASP.NET configurée d'authentification basée revendication\-.  Pour exécuter un test de base, vous ajouterez le code qui affiche des revendications dans le jeton émise par le service d'émission de jeton de sécurité \(STS\).  
  
#### Pour tester votre application web formes ASP.NET d'authentification basée revendication\-  
  
1.  Ouvrez le fichier de **Default.aspx** sous le projet de **TestApp** et remplacez son balisage existante par la balise suivante :  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2.  Enregistrez **Default.aspx**, puis ouvrez son code sous\-jacent **Default.aspx.cs**nommé par fichier.  
  
    > [!NOTE]
    >  **Default.aspx.cs** peut être masqué sous l'explorateur de **Default.aspx** de solutions.  Si **Default.aspx.cs** n'est pas visible, développez **Default.aspx** en cliquant sur le triangle en regard de celle\-ci.  
  
3.  Remplacez le code existant dans la méthode de **Page\_Load** de **Default.aspx.cs** par le code suivant :  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4.  Enregistrez **Default.aspx.cs**, et générez la solution.  
  
5.  Exécutez la solution en appuyant sur la touche de **F5** .  
  
6.  Vous devez être présenté avec la page qui affiche les revendications dans le jeton qui a été fournie à vous par le service d'émission de jeton de sécurité.