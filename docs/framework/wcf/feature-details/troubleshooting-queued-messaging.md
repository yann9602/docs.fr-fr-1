---
title: "R&#233;solution des probl&#232;mes de messagerie en file d&#39;attente | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# R&#233;solution des probl&#232;mes de messagerie en file d&#39;attente
Cette section contient les questions courantes et l'aide à la résolution des problèmes relatifs à l'utilisation des files d'attente dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## Questions courantes  
 **Q :** J'ai utilisé [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Bêta 1 et installé le correctif logiciel MSMQ.Est\-ce que je dois supprimer le correctif logiciel ?  
  
 **R :** Oui.Ce correctif logiciel n'est plus pris en charge.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fonctionne maintenant sur MSMQ sans spécification de correctif logiciel.  
  
 **Q :** Il existe deux liaisons pour MSMQ : <xref:System.ServiceModel.NetMsmqBinding> et <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.Laquelle dois\-je utiliser et à quel moment ?  
  
 **R :** Utilisez <xref:System.ServiceModel.NetMsmqBinding> lorsque vous souhaitez utiliser MSMQ en tant que transport pour les communications mises en file d'attente entre deux applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Utilisez <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> lorsque vous souhaitez utiliser des applications MSMQ existantes pour communiquer avec les nouvelles applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 **Q :** Dois\-je mettre à niveau MSMQ pour utiliser les liaisons <xref:System.ServiceModel.NetMsmqBinding> et `MsmqIntegration` ?  
  
 **R :** Non.Les deux liaisons fonctionnent avec MSMQ 3.0 sur [!INCLUDE[wxp](../../../../includes/wxp-md.md)] et [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].Certaines fonctionnalités des liaisons deviennent disponibles lorsque vous effectuez la mise à niveau vers MSMQ 4.0 dans [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 **Q :** Quelles fonctionnalités des liaisons <xref:System.ServiceModel.NetMsmqBinding> et <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sont disponibles dans MSMQ 4.0 mais indisponibles dans MSMQ 3.0 ?  
  
 **R :** Les fonctionnalités suivantes sont disponibles dans MSMQ 4.0 mais pas dans MSMQ 3.0 :  
  
-   La file d'attente de lettres mortes personnalisée est uniquement prise en charge sur MSMQ 4.0.  
  
-   MSMQ 3.0 et 4.0 gèrent les messages incohérents différemment.  
  
-   Seul MSMQ 4.0 prend en charge la lecture transactionnelle à distance.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Différences entre les fonctionnalités de mise en file d'attente dans Windows Vista, Windows Server 2003 et Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
 **Q :** Est\-ce que je peux utiliser MSMQ 3.0 à une extrémité d'une communication mise en file d'attente et MSMQ 4.0 à l'autre extrémité ?  
  
 **R :** Oui.  
  
 **Q :** Je souhaite intégrer des applications MSMQ existantes à de nouveaux clients ou serveurs [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Est\-ce que je dois mettre à niveau les deux côtés de mon infrastructure MSMQ ?  
  
 **R :** Non.Vous n'êtes pas obligé d'effectuer la mise à niveau vers MSMQ 4.0 sur l'un ou l'autre des côtés.  
  
## Résolution des problèmes  
 Cette section contient les solutions aux problèmes les plus courants.Certains problèmes correspondant à des restrictions connues sont également décrits dans les notes de version.  
  
 **Q :** J'essaie d'utiliser une file d'attente privée et j'obtiens l'exception suivante : `System.InvalidOperationException` : L'URL n'est pas valide.L'URL de la file d'attente ne peut pas contenir le caractère « $ ».Utilisez la syntaxe dans net.msmq:\/\/machine\/private\/queueName pour adresser une file d'attente privée.  
  
 **R :** Vérifiez l'URI \(Uniform Resource Identifier\) de la file d'attente dans votre configuration et votre code.N'utilisez pas le caractère « $ » dans l'URI.Par exemple, pour adresser une file d'attente privée nommée OrdersQueue, spécifiez l'URI comme net.msmq:\/\/localhost\/private\/ordersQueue.  
  
 **Q :** L'appel de `ServiceHost.Open()` sur mon application en file d'attente renvoie l'exception suivante : `System.ArgumentException` : Une adresse de base ne peut pas contenir une chaîne de requête URI.Pourquoi ?  
  
 **R :** Vérifiez l'URI de file d'attente dans votre fichier de configuration et dans votre code.Alors que les files d'attente MSMQ prennent en charge l'utilisation du caractère '?', les Uri interprètent ce dernier comme le début d'une requête de chaîne.Pour éviter ce problème, utilisez des noms de file d'attente qui ne comportent pas de caractère '?'.  
  
 **Q :** Mon envoi a réussi mais aucune opération de service n'est appelée sur le récepteur.Pourquoi ?  
  
 **R :** Pour déterminer la réponse, parcourez la liste de contrôle suivante :  
  
-   Vérifiez que les spécifications de la file d'attente transactionnelle sont compatibles avec les garanties spécifiées.Notez les principes suivants :  
  
    -   Vous pouvez envoyer des messages durables \(datagrammes et sessions\) avec des garanties « exactly\-once » \(<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> \= `true`\) uniquement à une file d'attente transactionnelle.  
  
    -   Vous pouvez envoyer des sessions uniquement avec des garanties « exactly\-once ».  
  
    -   Une transaction est requise pour recevoir des messages dans une session provenant d'une file d'attente transactionnelle.  
  
    -   Vous pouvez échanger \(envoyer et recevoir\) des messages volatiles ou durables \(datagrammes uniquement\) sans garanties \(<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> \= `false`\) uniquement avec une file d'attente non transactionnelle.  
  
-   Vérifiez la file d'attente de lettres mortes.Si vous y trouvez les messages, déterminez pourquoi ils n'ont pas été remis.  
  
-   Recherchez dans les files d'attente sortantes d'éventuels problèmes de connectivité ou d'adressage.  
  
 **Q :** J'ai spécifié une file d'attente de lettres mortes personnalisée, mais lorsque je démarre l'application émettrice, j'obtiens une exception qui stipule que la file d'attente de lettres mortes est introuvable ou que l'application émettrice ne possède pas d'autorisation d'accès à la file d'attente de lettres mortes.Pourquoi ?  
  
 **R :** L'URI de la file d'attente de lettres mortes personnalisée doit inclure « localhost » ou le nom de l'ordinateur dans le premier segment, par exemple, net.msmq:\/\/localhost\/private\/myAppdead\-letter queue.  
  
 **Q :** Est\-il toujours nécessaire de définir une file d'attente de lettres mortes personnalisée ou en existe\-t\-il une par défaut ?  
  
 **R :** Si les garanties sont des garanties « exactly\-once », \(<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> \= `true`\) et si vous ne spécifiez pas de file d'attente de lettres mortes personnalisée, une file d'attente de lettres mortes transactionnelle à l'échelle du système est définie par défaut.  
  
 Si les garanties n'existent pas \(<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> \= `false`\), aucune fonctionnalité de file d'attente de lettres mortes n'est définie par défaut.  
  
 **Q :** Mon service lève une exception sur SvcHost.Open avec un message indiquant que les spécifications EndpointListener ne peuvent pas être respectées par ListenerFactory.Pourquoi ?  
  
 R.Consultez votre contrat de service.Vous avez peut\-être oublié de mettre « IsOneWay \=`true` » sur toutes les opérations de service.Les files d'attente prennent uniquement en charge les opérations de service monodirectionnelles.  
  
 **Q :** La file d'attente contient des messages mais aucune opération de service n'est appelée.Quel est le problème ?  
  
 **R :** Déterminez si votre hôte de service provoque une erreur.Vous pouvez le vérifier en examinant le suivi ou en implémentant `IErrorHandler`.L'hôte de service provoque une erreur, par défaut, si un message incohérent est détecté.  
  
 **Q :** La file d'attente contient des messages mais mon service mis en file d'attente et hébergé sur le Web n'est pas activé.Pourquoi ?  
  
 **R :** La raison la plus courante implique les autorisations.  
  
1.  Vérifiez que le processus `NetMsmqActivator` s'exécute et que des autorisations de lecture et de recherche sont attribuées à l'identité du processus `NetMsmqActivator` sur la file d'attente.  
  
2.  Si `NetMsmqActivator` surveille les files d'attente sur un ordinateur distant, assurez\-vous que `NetMsmqActivator` ne s'exécute pas sous un jeton restreint.Pour exécuter `NetMsmqActivator` avec un jeton non restreint :  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 Pour les problèmes d'hôte Web qui ne sont pas liés à la sécurité, reportez\-vous à : [Hébergement sur le Web d'une application en file d'attente](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).  
  
 **Q :** Quelle est la manière la plus simple d'accéder aux sessions ?  
  
 **R :** Affectez à AutoComplete la valeur `true` sur l'opération correspondant au dernier message de la session et `false` sur toutes autres les opérations de service.  
  
 **Q :** Où puis\-je trouver les réponses aux questions courantes sur MSMQ ?  
  
 **R :** [!INCLUDE[crabout](../../../../includes/crabout-md.md)] MSMQ, consultez [Mise en file d'attente des messages Microsoft](http://go.microsoft.com/fwlink/?LinkId=87810).  
  
 **Q :** Pourquoi mon service lève\-t\-il une `ProtocolException` lors de la lecture d'une file d'attente contenant à la fois des messages de session et des messages de datagramme mis en file d'attente ?  
  
 **R :** Il existe une différence fondamentale dans la manière de rédiger des messages de session et des messages de datagramme mis en file d'attente.De ce fait, un service conçu pour lire un message de session en file d'attente ne peut pas recevoir de message de datagramme en file d'attente et un service conçu pour lire un message de datagramme en file d'attente ne peut pas recevoir de message de session.La tentative de lire les deux types de messages à partir de la même file d'attente lève l'exception suivante :  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 La file d'attente de lettres mortes du système, ainsi que toutes les files d'attente de lettres mortes personnalisées, sont particulièrement exposées à ce problème si une application envoie à la fois des messages de session en file d'attente et des messages de datagramme en file d'attente depuis le même ordinateur.Si un message ne peut pas être envoyé avec succès, il est déplacé vers la file d'attente de lettres mortes.Dans ces circonstances, il est possible d'avoir à la fois des messages de session et de datagramme dans la file d'attente de lettres mortes.Il n'existe aucun moyen de séparer les deux types de messages pendant l'exécution lors de la lecture à partir d'une file d'attente, par conséquent, les applications ne doivent pas envoyer à la fois des messages de session en file d'attente et des messages de datagramme en file d'attente depuis le même ordinateur.  
  
### Intégration de MSMQ : Dépannage spécifique  
 **Q :** Lorsque j'envoie un message ou lorsque j'ouvre l'hôte de service, j'obtiens une erreur qui indique que le modèle est incorrect.Pourquoi ?  
  
 **R :** Lorsque vous utilisez la liaison d'intégration MSMQ, vous devez utiliser le modèle msmq.formatname.Par exemple, msmq.formatname:DIRECT\=OS:.\\private$\\OrdersQueue.Mais lorsque vous spécifiez la file d'attente de lettres mortes personnalisée, vous devez utiliser le modèle net.msmq.  
  
 **Q :** Lorsque j'utilise un nom de format public ou privé et que j'ouvre l'hôte de service sur [!INCLUDE[wv](../../../../includes/wv-md.md)], j'obtiens une erreur.Pourquoi ?  
  
 **R :** Le canal d'intégration [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sur [!INCLUDE[wv](../../../../includes/wv-md.md)] vérifie si une sous\-file d'attente peut être ouverte pour la file d'attente d'application principale afin de gérer les messages empoisonnés.Le nom de la sous\-file d'attente est dérivé d'un URI msmq.formatname transmis à l'écouteur.Le nom de la sous\-file d'attente dans MSMQ peut uniquement être un nom de format direct.Donc vous obtenez l'erreur.Remplacez l'URI de la file d'attente par un nom de format direct.  
  
 **Q :** Lorsque je reçois un message d'une application MSMQ, il reste dans la file d'attente sans être lu par l'application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de réception.Pourquoi ?  
  
 **R :** Vérifiez si le message comporte un corps.Si le message n'a aucun corps, le canal d'intégration MSMQ l'ignore.Implémentez `IErrorHandler` pour être averti des exceptions et vérifiez les suivis.  
  
### Résolution des problèmes liés à la sécurité  
 **Q :** Lorsque j'exécute l'exemple qui utilise une liaison par défaut en mode groupe de travail, les messages semblent être envoyés mais ne sont jamais reçus par le destinataire.  
  
 **R :** Par défaut, les messages sont signés à l'aide d'un certificat interne MSMQ qui requiert le service d'annuaire Active Directory.En mode groupe de travail, parce qu'Active Directory n'est pas disponible, la signature des messages échoue.Donc les messages atterrissent dans la file d'attente de lettres mortes et un échec, tel qu'une mauvaise signature, est indiqué.  
  
 La solution à ce problème consiste à désactiver la sécurité.Pour cela, affectez la valeur <xref:System.ServiceModel.NetMsmqSecurityMode> à <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> pour obtenir un fonctionnement correct en mode groupe de travail.  
  
 Une autre solution consiste à obtenir <xref:System.ServiceModel.MsmqTransportSecurity> de la propriété <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> et à lui affecter la valeur <xref:System.ServiceModel.MsmqAuthenticationMode>, puis à définir le certificat client.  
  
 Une autre solution consiste à installer MSMQ avec l'intégration Active Directory.  
  
 **Q :** Lorsque j'envoie un message avec la liaison par défaut \(sécurité de transport activée\) dans Active Directory à une file d'attente, j'obtiens un message qui indique que le certificat interne est introuvable.Comment puis\-je résoudre ce problème ?  
  
 **R :** Cela signifie qu'il est nécessaire de renouveler le certificat dans Active Directory pour l'expéditeur.Pour cela, cliquez sur **Panneau de configuration**, **Outils d'administration**, **Gestion de l'ordinateur**, puis cliquez avec le bouton droit sur **MSMQ** et sélectionnez **Propriétés**.Sélectionnez l'onglet **Certificat utilisateur** et cliquez sur le bouton **Renouveler**.  
  
 **Q :** Lorsque j'envoie un message à l'aide de <xref:System.ServiceModel.MsmqAuthenticationMode> et que je spécifie le certificat à utiliser, j'obtiens un message qui indique que le certificat n'est pas valide.Comment puis\-je résoudre ce problème ?  
  
 **R :** Vous ne pouvez pas utiliser un magasin de certificats d'ordinateur local avec le mode certificat.Vous devez copier le certificat du magasin de certificats de l'ordinateur vers le magasin de l'utilisateur actuel à l'aide du composant logiciel enfichable Certificat.Pour obtenir le composant logiciel enfichable Certificat :  
  
1.  Cliquez sur **Démarrer**, sélectionnez **Exécuter**, tapez `mmc`, puis cliquez sur **OK**.  
  
2.  Dans **Microsoft Management Console**, ouvrez le menu **Fichier** et sélectionnez **Ajouter\/Supprimer un composant logiciel enfichable**.  
  
3.  Dans la boîte de dialogue **Ajouter\/Supprimer un composant logiciel enfichable**, cliquez sur le bouton **Ajouter**.  
  
4.  Dans la boîte de dialogue **Ajout d'un composant logiciel enfichable autonome**, sélectionnez Certificats et cliquez sur **Ajouter**.  
  
5.  Dans la boîte de dialogue du composant logiciel enfichable **Certificats**, sélectionnez **Mon compte d'utilisateur** et cliquez sur **Terminer**.  
  
6.  Ensuite, ajoutez un second composant logiciel enfichable Certificats à l'aide des étapes précédentes, mais cette fois, sélectionnez **Le compte de l'ordinateur**, puis cliquez sur **Suivant**.  
  
7.  Sélectionnez **Ordinateur local** et cliquez sur **Terminer**.Vous pouvez à présent déplacer des certificats depuis le magasin de certificats de l'ordinateur vers le magasin de l'utilisateur actuel.  
  
 **Q :** Lorsque mon service lit à partir d'une file d'attente sur un autre ordinateur en mode groupe de travail, j'obtiens une exception d'accès refusé.  
  
 **R :** En mode groupe de travail, pour qu'une application distante accède à la file d'attente, l'application doit avoir l'autorisation d'accéder à celle\-ci.Ajoutez « Connexion anonyme » à la liste de contrôle d'accès \(ACL, Access Control List\) de la file d'attente et attribuez\-lui une autorisation de lecture.  
  
 **Q :** Lorsqu'un client de service réseau \(ou tout client qui n'a pas de compte de domaine\) envoie un message en file d'attente, l'envoi échoue avec un certificat non valide.Comment puis\-je résoudre ce problème ?  
  
 **R :** Vérifiez la configuration de la liaison.Pour la liaison par défaut, la sécurité de transport MSMQ est activée afin de signer le message.Désactivez\-la.  
  
### Réceptions avec transactions distantes  
 **Q :** Lorsque j'ai une file d'attente sur l'ordinateur A et un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui lit les messages dans une file d'attente sur l'ordinateur B \(scénario de la réception avec transaction distante\), les messages ne sont pas lus à partir de la file d'attente.Les informations de suivi indiquent que la réception a échoué dans un message qui stipule qu'il n'est pas possible d'importer la transaction. Qu'est\-ce que je peux faire pour résoudre ce problème ?  
  
 **R :** Il existe trois raisons possibles à ce problème :  
  
-   Si vous êtes en mode domaine, la réception avec transaction distante requiert l'accès réseau MSDTC \(Microsoft Distributed Transaction Coordinator\).Vous pouvez activer cet accès à l'aide de la fonctionnalité **Ajouter\/Supprimer des composants**.  
  
     ![Activation de l'accès DTC réseau](../../../../docs/framework/wcf/feature-details/media/applicationserveraddcomps.jpg "ApplicationServerAddComps")  
  
-   Vérifiez le mode d'authentification pour communiquer avec le gestionnaire de transactions.Si vous êtes en mode groupe de travail, vous devez sélectionner Aucune authentification requise.Si vous êtes en mode domaine, vous devez sélectionner Authentification mutuelle requise.  
  
     ![Activation des transactions XA](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0\-fb0b\-4c5b\-afac\-75f8860d2bb0")  
  
-   Assurez\-vous que ce MSDTC figure dans la liste des exceptions dans les paramètres du **Pare\-feu de connexion Internet**.  
  
-   Vérifiez que vous utilisez [!INCLUDE[wv](../../../../includes/wv-md.md)].MSMQ sur [!INCLUDE[wv](../../../../includes/wv-md.md)] prend en charge la lecture avec transaction distante.MSMQ sur les versions antérieures de Windows ne prend pas en charge la lecture avec transaction distante.  
  
 **Q :** Quand le service qui lit à partir de la file d'attente est un service réseau, par exemple, sur un hôte Web, pourquoi est\-ce que j'obtiens une exception d'accès refusé lors de la lecture à partir de la file d'attente ?  
  
 **R :** L'accès en lecture du service réseau doit être ajouté à l'ACL de la file d'attente afin de veiller à ce qu'un service réseau puisse lire à partir de la file d'attente.  
  
 **Q :** Est\-ce que je peux utiliser le service d'activation MSMQ pour activer des applications basées sur des messages dans une file d'attente sur un ordinateur distant ?  
  
 **R :** Oui.Pour cela, vous devez configurer le service d'activation MSMQ afin qu'il s'exécute comme un service réseau, puis ajouter l'accès au service réseau à la file d'attente sur l'ordinateur distant.  
  
## Utilisation de liaisons MSMQ personnalisées avec ReceiveContext activé  
 Si vous utilisez une liaison MSMQ personnalisée avec <xref:System.ServiceModel.Channels.ReceiveContext> activé, le traitement d'un message entrant utilisera un thread de pool de threads car le protocole MSMQ natif ne prend pas en charge les ports de terminaison d'E\/S pour les réceptions <xref:System.ServiceModel.Channels.ReceiveContext> asynchrones.En effet, le traitement de ce message utilise des transactions internes pour <xref:System.ServiceModel.Channels.ReceiveContext> et  MSMQ ne prend pas en charge le traitement asynchrone.Pour contourner ce problème vous pouvez ajouter un <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> au point de terminaison pour forcer le traitement synchrone ou affecter la valeur 1 à la propriété <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A>.