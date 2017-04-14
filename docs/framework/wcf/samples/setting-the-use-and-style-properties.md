---
title: "Setting the Use and Style Properties | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# Setting the Use and Style Properties
Cet exemple illustre comment utiliser les propriétés Use et Style des attributs <xref:System.ServiceModel.XmlSerializerFormatAttribute> et <xref:System.ServiceModel.DataContractFormatAttribute>.  Ces propriétés affectent la manière dont les messages sont mis en forme.  Par défaut, la propriété de style, en fonction de laquelle le corps des messages est mis en forme, a pour valeur <xref:System.ServiceModel.OperationFormatStyle>.  Ces paramètres peuvent être spécifiés dans les contrats de service ou d'opération.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 La propriété de style <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> détermine la manière dont les métadonnées WSDL du service sont mises en forme.  Cette propriété peut avoir les valeurs suivantes : <xref:System.ServiceModel.OperationFormatStyle> et <xref:System.ServiceModel.OperationFormatStyle>.  RPC signifie que la représentation WSDL des messages échangés pour une opération contient des paramètres propres à un appel de procédure distante.  Voici un exemple.  
  
```  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
    <wsdl:part name="n1" type="xsd:double"/>  
    <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 Avec le style <xref:System.ServiceModel.OperationFormatStyle>, la représentation WSDL contient un élément unique qui représente le document échangé pour une opération, tel qu'illustré dans l'exemple suivant.  
  
```  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
    <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 La propriété <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> détermine la mise en forme des messages.  Les valeurs possibles de cette propriété sont <xref:System.ServiceModel.OperationFormatUse> et <xref:System.ServiceModel.OperationFormatUse>. Sa valeur par défaut est <xref:System.ServiceModel.OperationFormatUse>.  Cette dernière valeur signifie que le message correspond à une instance littérale du schéma dans le WSDL, tel qu'illustré dans l'exemple document\/littéral suivant.  
  
```  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
    <n1>100</n1>  
    <n2>15.99</n2>  
</Add>  
```  
  
 Encoded signifie que les schémas en WSDL sont des spécifications abstraites encodées selon les règles trouvées dans SOAP 1.1, section 5.  Voici un exemple de document RPC\/Encoded.  
  
```  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
    <n1 xsi:type="xsd:double" xmlns="">100</n1>  
    <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 Le profil WS\-I Basic Profile 1.0 ne permet pas d'utiliser <xref:System.ServiceModel.OperationFormatUse>. Vous devez uniquement utiliser ce profil lorsque requis par les services hérités.  Le format de message `Encoded` est disponible uniquement lorsque le sérialiseur XmlSerializer est utilisé.  
  
 Cet exemple est basé sur [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) afin que vous puissiez consulter les messages envoyés et reçus.  La configuration du service et le code source ont été modifiés pour activer le suivi et l'enregistrement des messages et permettre leur utilisation.  En outre, la liaison <xref:System.ServiceModel.WsHttpBinding> a été configurée sans mode de sécurité. Les messages enregistrés peuvent donc être affichés dans un format non chiffré.  Les journaux de suivis obtenus \(System.ServiceModel.e2e et Message.log\) doivent être affichés à l'aide de [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  Les suivis sont configurés de sorte à être créés dans le dossier C:\\LOGS.  Créez ce dossier avant d'exécuter l'exemple.  Pour consulter le contenu des messages à l'aide de l'outil Service Trace Viewer, sélectionnez **Messages** à la fois dans les volets de droite et de gauche de cet outil.  
  
 Dans le contrat de service défini par le code suivant, la propriété <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> a la valeur <xref:System.ServiceModel.OperationFormatUse> et le format du corps du message au lieu d'avoir la valeur par défaut <xref:System.ServiceModel.OperationFormatStyle> a la valeur <xref:System.ServiceModel.OperationFormatStyle>.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
XmlSerializerFormat(Style = OperationFormatStyle.Rpc,   
                                 Use = OperationFormatUse.Encoded)]  
public interface IUseAndStyleCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 Pour se rendre compte des différences existant entre les paramètres <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> et <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A>, modifiez\-les au niveau du service, régénérez le client, exécutez l'exemple, puis examinez le fichier c:\\logs\\message.logs à l'aide de l'outil Service Trace Viewer.  Observez également leur impact sur les métadonnées en consultant http:\/\/localhost\/ServiceModelSamples\/service.svc? wsdl.  En principe, les métadonnées des services sont réparties sur plusieurs pages.  La page wsdl principale contient les liaisons WSDL, mais ouvrez le fichier http:\/\/localhost\/ServiceModelSamples\/service.svc? wsdl\=wsdl0 afin d'observer les définitions de message.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Créez un répertoire C:\\LOGS pour l'enregistrement des messages.  Accordez à l'utilisateur des droits d'accès en écriture au service réseau pour ce répertoire.  
  
3.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## Voir aussi