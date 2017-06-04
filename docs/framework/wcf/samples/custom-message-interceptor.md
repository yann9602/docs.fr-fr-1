---
title: "Custom Message Interceptor | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
caps.latest.revision: 24
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 24
---
# Custom Message Interceptor
Cet exemple montre l'utilisation du modèle d'extensibilité des canaux.Plus précisément, il montre comment implémenter un élément de liaison personnalisé qui crée des fabrications et des écouteurs de canal pour intercepter tous les messages entrants et sortants à un point spécifique dans la pile d'exécution.L'exemple inclut également un client et serveur qui montrent l'utilisation de ces fabrications personnalisées.  
  
 Dans cet exemple, le client et le service sont tous deux des programmes de console \(.exe\).Le client et le service utilisent une bibliothèque commune \(.dll\) qui contient l'élément de liaison personnalisé et ses objets d'exécution associés.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 L'exemple décrit la procédure recommandée pour créer un canal superposé personnalisé dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], en utilisant l'infrastructure de canal et les meilleures pratiques [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suivantes.Les étapes de la création d'un canal superposé personnalisé sont les suivantes :  
  
1.  Déterminez les formes de canal que votre fabrication et écouteur de canal prendra en charge.  
  
2.  Créez une fabrication et un écouteur de canal qui prennent en charge vos formes de canal.  
  
3.  Ajoutez un élément de liaison qui ajoute le canal superposé personnalisé à une pile de canaux.  
  
4.  Ajoutez une section d'extension d'élément de liaison afin d'exposer le nouvel élément de liaison au système de configuration.  
  
## Formes de canal  
 La première étape de l'écriture d'un canal superposé personnalisé consiste à déterminer les formes requises pour le canal.Pour notre inspecteur de message, nous prenons en charge les formes qui la couche ci\-dessous prend en charge \(par exemple, si la couche ci\-dessous peux générer <xref:System.ServiceModel.Channels.IOutputChannel> et <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, nous exposons alors également <xref:System.ServiceModel.Channels.IOutputChannel> et <xref:System.ServiceModel.Channels.IDuplexSessionChannel>\).  
  
## Fabrication de canal et d'écouteur  
 L'étape suivante de l'écriture d'un canal superposé personnalisé consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IChannelFactory> pour les canaux clients et de <xref:System.ServiceModel.Channels.IChannelListener> pour les canaux de service.  
  
 Ces classes prennent une fabrication et un écouteur internes, puis leur délèguent tout les appels à l'exception de `OnCreateChannel` et `OnAcceptChannel`.  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## Ajout d'un élément de liaison  
 l'exemple définit un élément de liaison personnalisé : `InterceptingBindingElement`.`InterceptingBindingElement` prend `ChannelMessageInterceptor` comme entrée et utilise ce `ChannelMessageInterceptor` pour manipuler les messages qui le traversent.C'est la seule classe qui doit être publique.La fabrication, l'écouteur et les canaux peuvent tous être des implémentations internes des interfaces d'exécution publiques.  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## Ajout de la prise en charge de la configuration  
 Pour s'intégrer avec la configuration de liaison, la bibliothèque définit un gestionnaire de section de configuration comme section d'extension d'élément de liaison.Les fichiers de configuration du client et du serveur doivent enregistrer l'extension d'élément de liaison avec le système de configuration.Les implémenteurs qui souhaitent exposer leur élément de liaison au système de configuration peuvent dériver de cette classe.  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
  
```  
  
## Ajout d'une stratégie  
 Pour s'intégrer avec notre système de stratégie, `InterceptingBindingElement` implémente IPolicyExportExtension pour signaler que nous devons participer à la génération de la stratégie.Pour prendre en charge l'importation de la stratégie sur un client généré, l'utilisateur peut enregistrer une classe dérivée de `InterceptingBindingElementImporter` et substituer `CreateMessageInterceptor`\(\) pour générer leur classe `ChannelMessageInterceptor` activée par stratégie.  
  
## Exemple : Droppable Message Inspector  
 L'exemple comporte un exemple d'implémentation de `ChannelMessageInspector` qui supprime des messages.  
  
```  
  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Vous pouvez y accéder à partir de la configuration comme suit :  
  
```  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"   
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
  
```  
  
 Le client et le serveur utilisent cette section de configuration récemment créée afin dans d'insérer les fabrications personnalisées au niveau le plus bas de leurs piles d'exécution de canaux \(au\-dessus du niveau du transport\).  
  
```  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
  
```  
  
 Le client utilise la bibliothèque `MessageInterceptor` pour ajouter un en\-tête personnalisé aux messages portant un numéro pair.Le service utilise en revanche la bibliothèque `MessageInterceptor` pour supprimer les messages qui n'ont pas cet en\-tête spécifique.  
  
 La sortie du client suivante doit s'afficher après avoir exécuté le service puis le client.  
  
```  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
  
```  
  
 Le client signale 10 vitesses de vent différentes au service, mais n'en référence que la moitié avec l'en\-tête spécifique.  
  
 La sortie suivante doit s'afficher sur le service :  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
  
```  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Installez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 à l'aide de la commande suivante.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
  
    ```  
  
2.  Assurez\-vous d'avoir effectué la [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Pour générer la solution, suivez les instructions indiquées dans la rubrique [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions indiquées dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Exécutez d'abord Service.exe, puis Client.exe. Examinez ensuite la sortie dans les deux fenêtres de console.  
  
## Voir aussi