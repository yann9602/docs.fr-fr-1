---
title: "Comment&#160;: d&#233;boguer les probl&#232;mes d&#39;activation du CLR | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "activation des CLR, problèmes de débogage"
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: d&#233;boguer les probl&#232;mes d&#39;activation du CLR
Si vous rencontrez des problèmes en éxecutant votre application avec la version correcte du common langage runtime \(CLR\), vous pouvez afficher et déboguer des journaux de lancement du CLR.  Ces journaux peuvent être très utiles pour déterminer la cause première d'un problème de lancement, lorsque votre application charge une version CLR autre que prévue ou ne charge pas le CLR du tout.  [Erreurs d'initialisation de .NET Framework : gérer l'expérience utilisateur](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) décrit l'expérience lorsque aucun CLR n'est trouvé pour une application.  
  
 La journalisation du lancement du CLR peut être activé à l'échelle système grâce à une clé de Registre HKEY\_LOCAL\_MACHINE ou d'une variable d'environnement système.  Le journal sera généré jusqu'à ce que l'entrée du registre ou la variable d'environnement est supprimée.  Sinon, vous pouvez utiliser une variable d'environnement d'utilisateur ou de processus local pour activer la journalisation avec une portée et une durée différentes.  
  
 Les journaux de lancement du CLR ne doivent pas être confondus avec [journaux de liaison d'assembly](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), qui sont totallement différents.  
  
## Pour activer la journalisation de lancement du CLR  
  
#### Utiliser le Registre  
  
1.  Dans l'éditeur du registre, accédez au dossier HKEY\_LOCAL\_MACHINE \_\_ent\_dict\_AnyPathTillLastSlash \(sur un ordinateur 64 bits\).  
  
2.  Ajoutez une chaîne nommée `CLRLoadLogDir`, et définissez comme valeur le chemin d'accès complet d'un dossier existant dans lequel vous souhaitez stocker les journaux de lancement du CLR.  
  
 La ournalisation du lancement reste activé jusqu'à ce que vous supprimiez la valeur de la chaîne.  
  
#### Utiliser une variable d'environnement  
  
-   Définissez la variable d'environnement d' `COMPLUS_CLRLoadLogDir` une chaîne qui représente le chemin complet d'un dossier existant dans lequel vous souhaitez stocker des journaux de lancement du CLR.  
  
     La définition de la variable d'environnement détermine sa portée :  
  
    -   Si vous lui définissez au niveau du système, la journalisation du lancement est activé pour toutes les applications Framework .NET sur cet ordinateur jusqu'à ce que la variable d'environnement soit supprimée.  
  
    -   Si vous le configurez au niveau de l'utilisateur, la journalisation du lancement est activé uniquement pour le compte d'utilisateur actuel.  La journalisation se poursuit jusqu'à ce que la variable d'environnement soit supprimée.  
  
    -   Si vous le configurez dans processus avant de charger le CLR, la journalisation du lancement est activé jusqu'à ce que le processus se termine.  
  
    -   Si vous le configurez grâce à un invité de commande avant d'exécuter une application, la journalisation est activé pour toute application qui est exécutée dans cette invité de commande.  
  
     Par exemple, pour stocker les journaux d'activation dans le répértoire c:\\clrloadlogs avec une portée de niveau processus, ouvrir un invité de commande et tapez le texte suivant avant d'exécuter l'application :  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## Exemple  
 La journalisation d'activation du CLR proposent de grandes quantités de données sur l'activation du CLR et l'utilisation des API d'hébergement du CLR.  La plupart de ces données est utilisée en interne par Microsoft, mais certaines données peuvent également être utiles pour les développeurs, comme décrit dans cet article.  
  
 Le journal reflète l'ordre dans lequel les API d'hébergement du CLR sont appelées.  Il inclut également des informations utiles sur l'ensemble des runtimes installés détectés sur l'ordinateur.  Le format de journal d'activation du CLR n'est pas encore lui\-même documenté, mais peut être utilisé pour aider les développeurs qui doivent résoudre des problèmes de lancement du CLR.  
  
> [!NOTE]
>  Vous ne pouvez pas ouvrir un journal de lancement tant que le processus utilisant le CLR est en cours.  
  
> [!NOTE]
>  Les journaux de lancement du CLR ne sont pas localisés ; ils sont toujours générés dans la langue anglaise.  
  
 Dans l'exemple suivant d'un journal de lancement, la plupart des informations utiles sont mises en surbrillance et décrites après le journal.  
  
```  
532,205950.367,CLR Loading log for C:\Tests\myapp.exe   
532,205950.367,Log started at 4:26:12 PM on 10/6/2011   
532,205950.367,-----------------------------------   
532,205950.382,FunctionCall: _CorExeMain   
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}   
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}   
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0   
532,205950.382,Input values for ComputeVersionString follow this line   
532,205950.382,-----------------------------------   
532,205950.382,Default Application Name: C:\Tests\myapp.exe   
532,205950.382,IsLegacyBind is: 0   
532,205950.382,IsCapped is 0   
532,205950.382,SkuCheckFlags are 0   
532,205950.382,ShouldEmulateExeLaunch is 0   
532,205950.382,LegacyBindRequired is 0   
532,205950.382,-----------------------------------   
532,205950.382,Parsing config file: C:\Tests\myapp.exe   
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727   
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.   
532,205950.398,SEM_FAILCRITICALERRORS is set to 0   
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3   
532,205950.398,FunctionCall: RealDllMain. Reason: 0   
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0  
  
```  
  
-   **Le journal de chargement du CLR** fournit le chemin d'accès au fichier exécutable qui a démarré le processus qui a chargé le code managé.  Notez que cela peut être un hôte natif.  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
  
    ```  
  
-   **Le runtime installé** est un ensemble de versions du CLR installées sur l'ordinateur qui sont des candidats pour la demande de lancement.  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
  
    ```  
  
-   **généré avec la version** est la version du CLR qui a été utilisé pour générer le fichier binaire qui a été fournie à une méthode telle que [ICLRMetaHostPolicy::GetRequestedRuntime](../Topic/ICLRMetaHostPolicy::GetRequestedRuntime%20Method.md).  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
  
    ```  
  
-   **installation de fonctionnalité à la demande** fait référence à activer le .NET Framework 3.5 sur windows 8.  Pour plus d'informations sur les scénarios, consultez [Erreurs d'initialisation de .NET Framework : gérer l'expérience utilisateur](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md).  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
  
    ```  
  
## Voir aussi  
 [déploiement](../../../docs/framework/deployment/net-framework-and-applications.md)   
 [Comment : configurer une application pour prendre en charge le .NET Framework 4 ou 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)