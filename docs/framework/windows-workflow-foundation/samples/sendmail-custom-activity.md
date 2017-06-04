---
title: "Activit&#233; personnalis&#233;e SendMail | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Activit&#233; personnalis&#233;e SendMail
Cet exemple montre comment créer une activité personnalisée dérivée de <xref:System.Activities.AsyncCodeActivity> pour envoyer du courrier à l'aide de SMTP afin de l'utiliser dans une application de workflow.L'activité personnalisée utilise les fonctionnalités de <xref:System.Net.Mail.SmtpClient> pour envoyer du courrier électronique de façon asynchrone et envoyer du courrier avec authentification.Elle fournit aussi certaines fonctionnalités d'utilisateur final telles que le mode Test, le remplacement des jetons, les modèles de fichier et le chemin d'accès de dépôt de test.  
  
 Le tableau suivant décrit en détail les arguments pour l'activité `SendMail`.  
  
||||  
|-|-|-|  
|Nom|Type|Description|  
|Host|String|Adresse du serveur hôte SMTP.|  
|Port|String|Port du service SMTP dans l'hôte.|  
|EnableSsl|bool|Indique si <xref:System.Net.Mail.SmtpClient> utilise le protocole SSL \(Secure Sockets Layer\) pour chiffrer la connexion.|  
|UserName|String|Nom d'utilisateur pour définir les informations d'identification utilisées pour authentifier la propriété <xref:System.Net.Mail.SmtpClient.Credentials%2A> de l'expéditeur.|  
|Password|String|Mot de passe pour définir les informations d'identification utilisées pour authentifier la propriété <xref:System.Net.Mail.SmtpClient.Credentials%2A> de l'expéditeur.|  
|Subject|<xref:System.Activities.InArgument%601>\<string\>|Sujet du message.|  
|Body|<xref:System.Activities.InArgument%601>\<string\>|Corps du message.|  
|Attachments|<xref:System.Activities.InArgument%601>\<string\>|Collection de pièces jointes utilisée pour stocker des données jointes à ce message électronique.|  
|From|<xref:System.Net.Mail.MailAddress>|Adresse d'origine de ce message électronique.|  
|To|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>\>|Collection d'adresses qui contient les destinataires de ce message électronique.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>\>|Collection d'adresses qui contient les destinataires de copie carbone \(CC\) pour ce message électronique.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>\>|Collection d'adresses qui contient les destinataires de copie carbone invisible \(CCI\) pour ce message électronique.|  
|Tokens|<xref:System.Activities.InArgument%601>\<IDictionary\<string, string\>\>|Jetons à remplacer dans le corps.Cette fonctionnalité permet aux utilisateurs de spécifier certaines valeurs dans le corps qui peuvent être remplacées ultérieurement par les jetons fournis à l'aide de cette propriété.|  
|BodyTemplateFilePath|String|Chemin d'accès à un modèle de corps.L'activité `SendMail` copie le contenu de ce fichier dans sa propriété de corps.<br /><br /> Ce modèle peut contenir des jetons qui sont remplacés par le contenu de la propriété des jetons.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Lorsque cette propriété est définie, tous les courriers électroniques sont envoyés à l'adresse qu'elle indique.<br /><br /> Cette propriété n'est pas conçue pour une utilisation lors du test des workflows.Par exemple, assurez\-vous que tous les courriers électroniques sont envoyés sans les envoyer aux destinataires réels.|  
|TestDropPath|String|Lorsque cette propriété est définie, tous les courriers électroniques sont également enregistrés dans le fichier indiqué.<br /><br /> Cette propriété est conçue pour une utilisation lors du test ou débogage des workflows, pour vérifier que le format et le contenu des messages électroniques sortants sont appropriés.|  
  
## Contenu de la solution  
 La solution contient deux projets.  
  
|Projet|Description|Fichiers importants|  
|------------|-----------------|-------------------------|  
|SendMail|Activité SendMail|1.  SendMail.cs : implémentation pour l'activité principale<br />2.  SendMailDesigner.xaml et SendMailDesigner.xaml.cs : concepteur pour l'activité SendMail<br />3.  MailTemplateBody.htm : modèle pour le message électronique à envoyer.|  
|SendMailTestClient|Client pour tester l'activité SendMail.Ce projet illustre deux façons d'appeler l'activité SendMail : déclarative et par programme.|1.  Sequence1.xaml : workflow qui appelle l'activité SendMail.<br />2.  Program.cs : appelle Sequence1 et crée par programmation un workflow qui utilise SendMail.|  
  
## Configuration supplémentaire de l'activité SendMail  
 Bien qu'elle ne soit pas illustrée dans l'exemple, les utilisateurs peuvent effectuer une configuration supplémentaire de l'activité SendMail.Les trois sections suivantes montrent comment procéder.  
  
### Envoi d'un message électronique à l'aide de jetons spécifiés dans le corps  
 Cet extrait de code montre comment envoyer un message électronique avec des jetons dans le corps.Notez la façon dont les jetons sont fournis dans la propriété de corps.Les valeurs pour ces jetons sont fournies à la propriété de jetons.  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
  
```  
  
### Envoi d'un message électronique à l'aide d'un modèle  
 Cet extrait de code montre comment envoyer un message électronique à l'aide de jetons de modèle dans le corps.Notez que lorsque vous définissez la propriété `BodyTemplateFilePath`, il n'est pas nécessaire de fournir la valeur pour la propriété Body \(le contenu du modèle sera copié dans le corps\).  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
  
```  
  
### Envoi de messages électronique en mode Test  
 Cet extrait de code montre comment définir les deux propriétés de test : en définissant `TestMailTo` sur tous les messages qui seront envoyés à john.doe@contoso.con \(sans tenir compte des valeurs To, Cc, Bcc\).En définissant TestDropPath, tous les messages électroniques sortants seront aussi enregistrés dans le chemin d'accès fourni.Ces propriétés peuvent être définies indépendamment \(elles ne sont pas liées\).  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
  
```  
  
## Instructions d'installation  
 Vous devez avoir accès à un serveur SMTP pour cet exemple.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]l'installation d'un serveur SMTP, consultez les liens suivants.  
  
-   [Microsoft TechNet](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [Configuration du service SMTP \(IIS 6.0\)](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [IIS 7.0 : Configuration d'un courrier électronique SMTP](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [Procédure : installer le service SMTP](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Les émulateurs SMTP fournis par des tiers ne sont pas disponibles pour le téléchargement.  
  
##### Pour exécuter cet exemple  
  
1.  Dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution SendMail.sln.  
  
2.  Vérifiez que vous avez accès à un serveur SMTP valide.Consultez les instructions d'installation.  
  
3.  Configurez le programme avec l'adresse de votre serveur et les adresses d'expéditeur et de destinataire.  
  
     Pour exécuter correctement cet exemple, vous devrez peut\-être configurer la valeur des adresses d'expéditeur et de destinataire et l'adresse du serveur SMTP dans les fichiers  Program.cs et Sequence.xaml.Vous devrez modifier l'adresse à ces deux emplacements car le programme envoie les messages de différentes façons.  
  
4.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
5.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`  
  
## Voir aussi