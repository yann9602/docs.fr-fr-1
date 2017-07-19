---
title: "Instructions sur les pare-feu | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
caps.latest.revision: 32
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 32
---
# Instructions sur les pare-feu
Pour que les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fonctionnent, vous devez activer plusieurs ports ou programmes dans le pare\-feu.Un grand nombre d'exemples communique en utilisant des ports contenus dans la plage 8000\-8003, ainsi que le port 9000.Le pare\-feu est activé par défaut et empêche l'accès à ces ports.Pour activer le pare\-feu pour les exemples, exécutez l'une des procédures suivantes, selon vos besoins et votre environnement de sécurité :  
  
-   Option 1: Activation interactive des exemples en cours d'exécution.N'apportez aucune modification à l'avance à votre configuration de pare\-feu et lancez la création et l'exécution des exemples.Lorsqu'un exemple est exécuté, une boîte de dialogue **Alerte de sécurité Windows** apparaît.L'exemple de programme en question peut ensuite être ajouté interactivement à une liste non bloquée.Dans le cadre de cette procédure, vous devrez peut\-être redémarrer l'exemple.  
  
-   Option 2: Activation des exemples de programmes à l'avance.Démarrez l'applet **Pare\-feu Windows \- Panneau de configuration** et activez les exemples de programmes que vous projetez d'exécuter.Vous devez générer en premier les programmes afin que les fichiers exécutables existent.Vous trouverez des instructions plus détaillées dans la procédure suivante.  
  
-   Option 3: Activation d'une plage de ports à l'avance.Lancez l'applet **Pare\-feu Windows** **Panneau de configuration** et activez les ports 80, 443, 8000\-8003 et 9000 \(ports utilisés par les exemples\).Vous trouverez des instructions plus détaillées dans la procédure suivante.Cette option est moins sécurisée que les autres, car elle permet à tout programme d'utiliser ces ports, et non aux exemples uniquement.  
  
 Si vous ne savez pas quelle procédure utiliser, choisissez la première option.Si vous utilisez le pare\-feu d'un autre fournisseur, vous devrez peut\-être apporter des modifications semblables.  
  
> [!IMPORTANT]
>  La modification de votre configuration de pare\-feu affecte votre sécurité.Il est recommandé d'enregistrer les modifications apportées et de les supprimer lorsque vous n'utilisez plus les exemples.  
  
### Pour activer à l'avance les programmes d'exemples  
  
1.  Créez un exemple.  
  
2.  Cliquez sur **Démarrer**, sur **Exécuter** et tapez `firewall.cpl`.Cela permet d'ouvrir l'applet **Pare\-feu Windows \- Panneau de configuration**.  
  
    > [!NOTE]
    >  Pour exécuter des exemples qui requièrent la capacité de communiquer via le Pare\-feu Windows, vous devez disposer des autorisations nécessaires pour modifier les paramètres du Pare\-feu Windows.Si certains paramètres du pare\-feu ne sont pas disponibles et que votre ordinateur est connecté à un domaine, il est possible que votre administrateur système contrôle ces paramètres au moyen d'une stratégie de groupe.  
  
3.  Effectuez l'une des étapes suivantes, selon votre système d'exploitation, pour autoriser un programme via le Pare\-feu Windows :  
  
    -   Sur Windows 7 ou Windows Server 2008 R2, cliquez sur **Autoriser un programme ou une fonctionnalité via le Pare\-feu Windows**.Cliquez sur **Modifier les paramètres**, puis sur **Autoriser un autre programme**.  
  
    -   Sur [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], cliquez sur **Autoriser un programme via le Pare\-feu Windows**.  
  
4.  Cliquez sur **Ajouter un programme** dans l'onglet **Exceptions**.  
  
5.  Cliquez sur le bouton **Parcourir** et sélectionnez le fichier exécutable de l'exemple que vous projetez d'exécuter.  
  
6.  Répétez des étapes 4 et 5 jusqu'à ce que vous ayez ajouté les fichiers exécutables de tous les exemples que vous souhaitez exécuter.  
  
7.  Cliquez sur **OK** pour fermer l'applet de pare\-feu.  
  
### Pour activer une plage de ports à l'avance  
  
1.  Cliquez sur **Démarrer**, sur **Exécuter** et tapez `firewall.cpl`.Cela permet d'ouvrir l'applet **Pare\-feu Windows \- Panneau de configuration**.  
  
2.  Sur Windows 7 ou Windows Server 2008 R2, procédez comme suit.  
  
    1.  Cliquez sur **Paramètres avancés** dans la colonne de gauche de la fenêtre Pare\-feu Windows.  
  
    2.  Cliquez sur **Règles de trafic entrant** dans la colonne de gauche.  
  
    3.  Cliquez sur **Nouvelle règle** dans la colonne de droite.  
  
    4.  Sélectionnez **Port** et cliquez sur **Suivant**.  
  
    5.  Sélectionnez **TCP** et entrez `8000, 8001, 8002, 8003, 9000, 80, 443` dans le champ **Ports locaux spécifiques**.  
  
    6.  Cliquez sur **Suivant**.  
  
    7.  Sélectionnez **Autoriser la connexion** et cliquez sur **Suivant**.  
  
    8.  Sélectionnez **Domaine** et **Privé**, pus cliquez sur **Suivant**.  
  
    9. Nommez cette règle `WCF-WF 4.0 Samples` et cliquez sur **Terminer**.  
  
    10. Cliquez sur **Règles de trafic sortant** et répétez les étapes c à h.  
  
3.  Sur [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], procédez comme suit.  
  
    1.  Cliquez sur **Autoriser un programme via le Pare\-feu Windows**.  
  
    2.  Cliquez sur **Ajouter un port** dans l'onglet **Exceptions**.  
  
    3.  Entrez un nom et le numéro de port 8000, puis sélectionnez l'option **TCP**.  
  
    4.  Cliquez sur le bouton **Modifier l'étendue**, sélectionnez l'option **Mon réseau** \(sous\-réseau\) et cliquez sur **OK**.  
  
    5.  Répétez les étapes b à d pour les ports 8001, 8002, 8003, 9000, 80 et 443.  
  
4.  Cliquez sur **OK** pour fermer l'applet de pare\-feu.  
  
> [!NOTE]
>  Supprimez toutes les exceptions de pare\-feu une fois que vous n'utilisez plus les exemples.Pour cela, ouvrez l'applet **Pare\-feu Windows \- Panneau de configuration** et supprimez tous programmes ou entrées de port ajoutés par les procédures précédentes.