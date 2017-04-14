---
title: "R&#233;solution des probl&#232;mes li&#233;s aux installations et d&#233;sinstallations de .NET&#160;Framework bloqu&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework, résolution des problèmes liés aux installations bloquées"
  - "installations du .NET Framework bloquées, dépanner"
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
caps.latest.revision: 57
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 39
---
# R&#233;solution des probl&#232;mes li&#233;s aux installations et d&#233;sinstallations de .NET&#160;Framework bloqu&#233;es
Quand vous exécutez le [programme d’installation web ou hors connexion](../../../docs/framework/install/guide-for-developers.md) pour .NET Framework 4.5, 4.5.1, 4.5.2, 4.6 ou 4.6.1, vous pouvez rencontrer un problème qui empêche ou bloque l’installation du .NET Framework. Le tableau suivant répertorie les problèmes possibles et fournit des liens vers des informations de dépannage.  
  
 Dans ce tableau, 4.5.*x* se rapporte à .NET Framework 4.5 et à ses versions intermédiaires, 4.5.1 et 4.5.2, 4.6 ou 4.6.1.  
  
|Message bloquant|Pour plus d'informations ou pour résoudre le problème|  
|----------------------|-----------------------------------------------------------|  
|La désinstallation du Microsoft .NET Framework peut interrompre le fonctionnement de certaines applications.|En général, vous ne devez pas désinstaller les versions du .NET Framework installées sur votre ordinateur, car une application que vous utilisez peut dépendre d'une version spécifique du .NET Framework. Pour plus d’informations, consultez [Le .NET Framework pour les utilisateurs](../../../docs/framework/get-started/index.md#ForUsers) dans le guide *Prise en main*.|  
|.NET Framework 4.5*.x*\/4.6*.x* \(*langue*\) nécessite .NET Framework 4.5*.x*\/4.6*.x*. Installez .NET Framework 4.5*.x*\/4.6*.x* à partir du Centre de téléchargement, puis réexécutez l’installation.|Vous devez installer la version anglaise du .NET Framework spécifié avant d'installer un module linguistique. Pour plus d’informations, consultez la section relative aux [Pour installer les modules linguistiques](../../../docs/framework/install/guide-for-developers.md#standalone_language_packs) dans le guide d’installation.|  
|Impossible d’installer .NET Framework 4.5*.x*\/4.6*.x*. D'autres applications installées sur cet ordinateur ne sont pas compatibles avec ce programme.<br /><br /> ou<br /><br /> D'autres applications installées sur cet ordinateur ne sont pas compatibles avec ce programme.|La cause la plus probable de ce message est qu'une version d'évaluation ou RC du .NET Framework a été installée. Désinstallez la version d'évaluation ou RC et réexécutez le programme d'installation.|  
|Impossible de désinstaller .NET Framework 4.5*.x*\/4.6*.x* avec ce package. Pour désinstaller .NET Framework 4.5*.x*\/4.6*.x* de votre ordinateur, ouvrez le **Panneau de configuration**, choisissez **Programmes et fonctionnalités**, **Afficher les mises à jour installées**, sélectionnez Mise à jour pour Microsoft Windows \(KB2828152\), puis choisissez **Désinstaller**.|Le package que vous installez ne désinstalle pas les versions d'évaluation ou RC du .NET Framework.<br /><br /> Désinstallez la version d'évaluation ou RC à partir du Panneau de configuration.|  
|Impossible de désinstaller .NET Framework 4.5*.x*\/4.6*.x*. D'autres applications installées sur votre ordinateur dépendent de ce programme.|En général, vous ne devez pas désinstaller les versions du .NET Framework de votre ordinateur car une application que vous utilisez peut dépendre d'une version spécifique du .NET Framework. Pour plus d’informations, consultez [Le .NET Framework pour les utilisateurs](../../../docs/framework/get-started/index.md#ForUsers) dans le guide *Prise en main*.|  
|Le redistribuable .NET Framework 4.5*.x*\/4.6*.x* ne s’applique pas à ce système d’exploitation. Téléchargez .NET Framework 4.5*.x*\/4.6*.x* pour votre système d’exploitation à partir du Centre de téléchargement Microsoft.|Vous essayez peut\-être d’installer [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6 ou 4.6.1 sur une plateforme qui n’est pas prise en charge ou vous avez choisi le package d’installation qui n’inclut pas les composants pour tous les systèmes d’exploitation pris en charge. Réexécutez l’installation en utilisant le programme d’installation hors connexion \([pour 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=309493), [4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706), [4.6](http://go.microsoft.com/fwlink/p/?LinkId=528233) ou [4.6.1](http://go.microsoft.com/fwlink/p/?LinkId=671744)\). Pour plus d'informations, voir le [guide d'installation](../../../docs/framework/install/guide-for-developers.md) et la [configuration système requise](../../../docs/framework/get-started/system-requirements.md) pour connaître les systèmes d'exploitation pris en charge.|  
|Votre ordinateur exécute actuellement une installation Server Core du système d'exploitation Windows Server 2008. Le .NET Framework 4.5.*x* requiert une version plus récente du système d'exploitation. Installez Windows Server 2008 R2 SP1 ou une version ultérieure, puis réexécutez le programme d'installation du .NET Framework 4.5.*x*.|Les [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] et 4.5.2 sont pris en charge dans le rôle principal du serveur avec Windows Server 2008 R2 SP1 ou une version ultérieure. Consultez [Configuration requise](../../../docs/framework/get-started/system-requirements.md).|  
|Vous ne disposez pas de privilèges suffisants pour effectuer cette opération pour l'ensemble des utilisateurs de cet ordinateur. Ouvrez une session en tant qu'administrateur et réexécutez l'**installation**.|Vous devez être administrateur de l'ordinateur pour installer le .NET Framework.|  
|Impossible de poursuivre l'installation, car une installation antérieure requiert le redémarrage de l'ordinateur. Redémarrez l'ordinateur et réexécutez le programme d'installation.|Un redémarrage est parfois nécessaire pour terminer complètement une installation. Suivez les instructions pour redémarrer votre ordinateur et réexécutez le programme d'installation.|  
|.NET Framework 4.5*.x*\/4.6*.x* \(FRA\) ou une mise à jour ultérieure est déjà installée sur cet ordinateur.|Aucune action n'est nécessaire.|  
|Le programme d'installation du .NET Framework ne peut pas être exécuté en mode de compatibilité des programmes.|Consultez la section [Problèmes de compatibilité entre les programmes](#compat) plus loin dans cet article.|  
|Le .NET Framework 4.5*.x*\/4.6*.x* n’a pas été installé car le magasin de composants a été endommagé.|Pour plus d’informations, consultez [Fix Windows Update errors by using the DISM or System Update Readiness tool](https://support.microsoft.com/en-us/kb/947821).|  
|Impossible d'exécuter le programme d'installation car le service Windows Installer n'est pas disponible sur cet ordinateur.|Consultez [Erreur « Impossible d’accéder au Service Windows Installer » lorsque vous essayez d’installer un programme sous Windows 7 ou Windows Vista](http://go.microsoft.com/fwlink/p/?LinkId=248684) sur le site web Support technique de Microsoft.|  
|Le programme d'installation peut ne pas s'exécuter correctement car le service Windows Update n'est pas disponible sur cet ordinateur.|L'ordinateur peut être configuré pour utiliser Windows Server Update Services \(WSUS\) au lieu de Microsoft Windows Update. Pour plus d’informations, consultez la section relative au code d’erreur 0x800F0906 de l’article [Codes d’erreur lorsque vous essayez d’installer .NET Framework 3.5 sous Windows 8 ou Windows Server 2012](http://support.microsoft.com/kb/2734782).<br /><br /> Consultez également l’article [Comment obtenir la version la plus récente de l’agent Windows Update de gestion des mises à jour](http://go.microsoft.com/fwlink/p/?LinkId=248437), disponible sur le site web Support technique de Microsoft.|  
|Le programme d'installation peut ne pas s'exécuter correctement car le service de transfert intelligent en arrière\-plan n'est pas disponible sur cet ordinateur.|Consultez l’article [Mise à jour afin visant à empêcher une panne du service de transfert intelligent en arrière\-plan \(BITS\) sur un ordinateur Windows Vista](http://go.microsoft.com/fwlink/p/?LinkId=248680), disponible sur le site web Support technique de Microsoft.|  
|.NET Framework 4.5*.x*\/4.6 fait déjà partie de ce système d’exploitation. Vous n’avez pas à installer le redistribuable .NET Framework 4.5*.x*\/4.6.|Aucune action. Consultez [Configuration requise](../../../docs/framework/get-started/system-requirements.md) pour connaître les systèmes d’exploitation pris en charge.|  
|.NET Framework 4.5*.x*\/4.6*.x* n’est pas pris en charge sur ce système d’exploitation.|Consultez [Configuration requise](../../../docs/framework/get-started/system-requirements.md) pour connaître les systèmes d’exploitation pris en charge.<br /><br /> Pour les installations du .NET Framework sur Windows 7 qui ont échoué, ce message indique généralement que Windows 7 SP1 n’est pas installé. Sur les systèmes Windows 7, le .NET Framework nécessite Windows 7 SP1. Si vous êtes sur Windows 7 et que vous n’avez pas encore installé le Service Pack 1, vous devez le faire avant d’installer le .NET Framework.|  
|Votre ordinateur exécute actuellement une installation minimale du système d'exploitation Windows Server 2008. Le .NET Framework 4.5.*x* requiert une version complète du système d'exploitation ou Server Core 2008 R2 SP1. Installez la version complète de Windows Server 2008 SP2, Windows Server 2008 R2 SP1 ou Server Core 2008 R2 SP1 et réexécutez le programme d'installation du .NET Framework 4.5.*x*.|Le .NET Framework est pris en charge dans le rôle principal du serveur avec Windows Server 2008 R2 SP1 ou une version ultérieure. Consultez [Configuration requise](../../../docs/framework/get-started/system-requirements.md).|  
|Le .NET Framework 4.5.*x* fait déjà partie de ce système d'exploitation, mais il est actuellement désactivé \([!INCLUDE[winserver8](../../../includes/winserver8-md.md)] uniquement\).|Consultez [Activer ou désactiver des fonctionnalités Windows](http://go.microsoft.com/fwlink/p/?LinkId=248438) sur le site web de Windows.|  
|Impossible d'exécuter ce programme d'installation sur un ordinateur x64 ou IA64. Le programme d'installation requiert un ordinateur x86.|Consultez [Configuration requise](../../../docs/framework/get-started/system-requirements.md) dans MSDN Library.|  
|Impossible d'exécuter ce programme d'installation sur un ordinateur IA64. Il ne peut pas être installé sur les ordinateurs IA64.|Consultez [Configuration requise](../../../docs/framework/get-started/system-requirements.md) dans MSDN Library.|  
  
<a name="compat"></a>   
### Problèmes de compatibilité entre les programmes  
 L'installation du .NET Framework 4.5 ou de ses versions intermédiaires échoue avec un code d'erreur 1603 ou se bloque quand elle est exécutée en mode de compatibilité des programmes Windows. L'**Assistant Compatibilité des programmes** indique qu'il est possible que .NET Framework n'ait pas été installé correctement. Il vous invite à le réinstaller à l'aide du paramètre recommandé \(mode de compatibilité des programmes\). Le mode de compatibilité des programmes peut également avoir été défini par l'Assistant Compatibilité des programmes lors de tentatives défectueuses ou annulées précédentes d'exécution du programme d'installation .NET Framework.  
  
 Le programme d'installation .NET Framework ne peut pas être exécuté en mode de compatibilité des programmes. Pour résoudre cette erreur majeure, vous devez vérifier que le paramètre de mode de compatibilité n'est pas activé au niveau du système dans l'Éditeur du Registre :  
  
1.  Choisissez le bouton **Démarrer**, puis sélectionnez **Exécuter**.  
  
2.  Dans la boîte de dialogue **Exécuter**, tapez `regedit`, puis cliquez sur **OK**.  
  
3.  Dans l'Éditeur du Registre, parcourez les sous\-clés suivantes :  
  
    -   HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AppCompatFlags\\Compatibility Assistant\\Persisted  
  
    -   HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AppCompatFlags\\Layers  
  
4.  Dans la colonne Nom, recherchez les noms de téléchargement [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6 ou 4.6.1, selon la version que vous installez, puis supprimez ces entrées. Pour les noms de téléchargement, consultez l’article [Guide d'installation](../../../docs/framework/install/guide-for-developers.md).  
  
5.  Réexécutez le programme d’installation du .NET Framework pour la version 4.5, 4.5.1, 4.5.2, 4.6 ou 4.6.1.  
  
## Voir aussi  
 [Guide d'installation](../../../docs/framework/install/guide-for-developers.md)