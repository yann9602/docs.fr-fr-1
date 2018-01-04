---
title: WSStreamedHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d6259640bae2b4be4fac73883df8945bf1db7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
Cet exemple montre comment créer une liaison conçue pour prendre en charge des scénarios de diffusion en continu lorsque le transport HTTP est utilisé.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 Les étapes de la création et de la configuration d’une nouvelle liaison standard sont les suivantes.  
  
1.  Créez une liaison standard  
  
     Les liaisons standard dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] telles que basicHttpBinding et netTcpBinding configurent les transports sous-jacents et la pile de canaux pour des besoins spécifiques. Dans cet exemple, `WSStreamedHttpBinding` configure la pile de canaux pour prendre en charge la diffusion en continu. Par défaut, WS-Security et messagerie fiable ne sont pas ajoutés à la pile de canaux car ces deux fonctionnalités ne sont pas prises en charge par la diffusion en continu. La nouvelle liaison est implémentée dans la classe `WSStreamedHttpBinding` qui dérive de <xref:System.ServiceModel.Channels.Binding>. `WSStreamedHttpBinding` contient les éléments de liaison suivants : <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> et <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. La classe fournit une méthode `CreateBindingElements()` permettant de configurer la pile de liaison résultante, tel qu'indiqué dans l'exemple de code suivant.  
  
    ```  
    public override BindingElementCollection CreateBindingElements()  
    {  
         // return collection of BindingElements  
         BindingElementCollection bindingElements = new BindingElementCollection();  
  
        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by  
        // the message encoder, and finally the transport at the end  
        if (flowTransactions)  
        {  
            bindingElements.Add(transactionFlow);  
        }  
        bindingElements.Add(textEncoding);  
  
        // add transport (http or https)  
        bindingElements.Add(transport);  
        return bindingElements.Clone();  
    }  
    ```  
  
2.  Ajoutez la prise en charge de la configuration  
  
     Pour exposer le transport via la configuration, l'exemple implémente deux classes : `WSStreamedHttpBindingConfigurationElement` et `WSStreamedHttpBindingSection`. La classe `WSStreamedHttpBindingSection` est un <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> qui expose `WSStreamedHttpBinding` au système de configuration [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Le bloc de l'implémentation est délégué à `WSStreamedHttpBindingConfigurationElement`, qui dérive de <xref:System.ServiceModel.Configuration.StandardBindingElement>. La classe `WSStreamedHttpBindingConfigurationElement` a des propriétés qui correspondent à celles de `WSStreamedHttpBinding`, et des fonctions pour mapper chaque élément de configuration à une liaison.  
  
     Pour enregistrer le gestionnaire avec le système de configuration, ajoutez la section suivante au fichier de configuration du service.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <extensions>  
          <bindingExtensions>  
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </bindingExtensions>  
        </extensions>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Il pourra ensuite être référencé à partir de la section de configuration serviceModel.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint  
                    address="https://localhost/servicemodelsamples/service.svc"  
                    bindingConfiguration="Binding"  
                    binding="wsStreamedHttpBinding"  
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Installez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 à l'aide de la commande suivante.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Vérifiez que vous avez effectué les étapes répertoriées dans [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Assurez-vous d’avoir effectué la [Instructions d’Installation du certificat serveur Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Pour exécuter l’exemple dans une configuration à plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6.  Lorsque la fenêtre du client s'affiche, tapez « Sample.txt ». Vous devez rechercher « Copy of Sample.txt » dans votre répertoire.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>Exemple de service WSStreamedHttpBinding  
 L'exemple de service qui utilise `WSStreamedHttpBinding` se trouve dans le sous-répertoire de service. L'implémentation de `OperationContract` utilise un `MemoryStream` pour récupérer dans un premier temps toutes les données du flux entrant avant de retourner `MemoryStream`. L'exemple de service est hébergé par les services IIS (Internet Information Services).  
  
```  
[ServiceContract]  
public interface IStreamedEchoService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
}  
  
public class StreamedEchoService : IStreamedEchoService  
{  
    public Stream Echo(Stream data)  
    {  
        MemoryStream dataStorage = new MemoryStream();  
        byte[] byteArray = new byte[8192];  
        int bytesRead = data.Read(byteArray, 0, 8192);  
        while (bytesRead > 0)  
        {  
            dataStorage.Write(byteArray, 0, bytesRead);  
            bytesRead = data.Read(byteArray, 0, 8192);  
        }  
        data.Close();  
        dataStorage.Seek(0, SeekOrigin.Begin);  
  
        return dataStorage;  
    }  
}  
```  
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>Exemple de client WSStreamedHttpBinding  
 Le client utilisé pour interagir avec le service à l'aide de `WSStreamedHttpBinding` se trouve dans le sous-répertoire client. Le certificat utilisé dans cet exemple étant un certificat de test créé avec Makecert.exe, une alerte de sécurité s'affiche lorsque vous tentez d'accéder depuis votre navigateur à une adresse HTTPS telle que https://localhost/servicemodelsamples/service.svc. Pour permettre au client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] d'utiliser un certificat de test en vigueur, du code supplémentaire a été ajouté au client pour supprimer l'alerte de sécurité. Le code, et la classe qui l'accompagne, ne sont pas requis lors de l'utilisation de certificats de production.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
## <a name="see-also"></a>Voir aussi
