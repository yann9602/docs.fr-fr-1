---
title: "Fonction d'hébergement du CLR déconseillées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9530fecb4f2ca6f59d165e49c282320966fd2fa8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="deprecated-clr-hosting-functions"></a>Fonction d'hébergement du CLR déconseillées
Cette section décrit les fonctions statiques globales non managées qui utilisées par les versions antérieures de l’API d’hébergement.  
  
 À l’exception des fonctions d’infrastructure (`_Cor*` fonctions), qui sont utilisés uniquement par le .NET Framework, ces fonctions ont été déconseillées dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="activation-functions"></a>Fonctions d’activation  
 [ClrCreateManagedInstance (fonction)](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 Obsolète. Crée une instance du type managé spécifié.  
  
 [CoInitializeCor (fonction)](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 Obsolète. Pour initialiser le common language runtime (CLR), utilisez [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
 [CoInitializeEE (fonction)](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 Obsolète. Garantit que le moteur d’exécution de CLR est chargé dans un processus. Utilisez le [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) méthode à la place.  
  
 [CorBindToCurrentRuntime (fonction)](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 Obsolète. Charge le common language runtime (CLR) dans un processus à l’aide des informations de version stockées dans un fichier XML.  
  
 [CorBindToRuntime (fonction)](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 Obsolète. Permet aux hôtes non managés de charger le CLR dans un processus.  
  
 [CorBindToRuntimeByCfg, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 Obsolète. Charge le CLR dans un processus à l’aide des informations de version qui sont lu à partir d’un fichier XML.  
  
 [CorBindToRuntimeEx (fonction)](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 Obsolète. Permet les hôtes non managés de charger le CLR dans un processus et vous permet de définir des indicateurs pour spécifier le comportement du CLR.  
  
 [CorBindToRuntimeHost (fonction)](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 Obsolète. Permet aux hôtes de charger une version spécifiée du CLR dans un processus.  
  
 [GetCORRequiredVersion (fonction)](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 Obsolète. Obtient le numéro de version CLR requis.  
  
 [GetCORSystemDirectory (fonction)](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 Obsolète. Retourne le répertoire d’installation du CLR qui est chargé dans le processus.  
  
 [GetRealProcAddress (fonction)](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 Obsolète. Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée du CLR.  
  
 [GetRequestedRuntimeInfo (fonction)](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 Obsolète. Obtient les informations de version et au répertoire sur le CLR demandé par une application.  
  
## <a name="clr-version-functions"></a>Fonctions de version CLR  
 Les fonctions de cette section retournent de la version CLR ; ils ne pas activent le CLR.  
  
 [GetCORVersion (fonction)](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 Obsolète. Retourne le numéro de version du CLR qui s’exécute dans le processus en cours.  
  
 [GetFileVersion (fonction)](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 Obsolète. Obtient les informations de version CLR du fichier spécifié, à l’aide de la mémoire tampon spécifiée.  
  
 [GetRequestedRuntimeVersion (fonction)](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 Obsolète. Obtient le numéro de version du CLR demandé par l’application spécifiée. Si cette version n’est pas installée, obtient la version la plus récente qui est installée avant la version demandée.  
  
 [GetRequestedRuntimeVersionForCLSID (fonction)](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 Obsolète. Obtient les informations de version CLR appropriées pour la classe avec le CLSID spécifié.  
  
 [GetVersionFromProcess (fonction)](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 Obsolète. Obtient le numéro de version du CLR qui est associé au handle de processus spécifié.  
  
 [LockClrVersion (fonction)](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 Obsolète. Permet à l’hôte déterminer quelle version du CLR sera utilisée au sein du processus avant d’initialiser le CLR explicitement.  
  
## <a name="hosting-functions"></a>Fonctions d’hébergement  
 [CallFunctionShim (fonction)](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 Obsolète. Effectue un appel à la fonction qui porte le nom spécifié et les paramètres dans la bibliothèque spécifiée.  
  
 [CoEEShutDownCOM (fonction)](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 Obsolète. Décharge un assembly COM du processus.  
  
 [CorExitProcess (fonction)](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 Obsolète. Arrête le processus non managé en cours.  
  
 [CorLaunchApplication (fonction)](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 Obsolète. Démarre l’application sur le chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et autres données d’application.  
  
 [CorMarkThreadInThreadPool (fonction)](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 Obsolète. Marque le thread de pool de threads en cours d’exécution pour l’exécution du code managé. À compter de .NET Framework version 2.0, cette fonction n’a aucun effet. Il n’est pas nécessaire et peut être supprimé de votre code.  
  
 [CoUninitializeCor (fonction)](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 Obsolète. Le CLR ne peut pas être déchargé d’un processus.  
  
 [CoUninitializeEE (fonction)](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 Obsolète.  
  
 [CreateDebuggingInterfaceFromVersion (fonction)](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 Obsolète. Crée un [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objet basé sur les informations de version spécifié.  
  
 [CreateICeeFileGen (fonction)](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 Obsolète. Crée un [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objet.  
  
 [DestroyICeeFileGen (fonction)](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 Obsolète. Détruit un [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objet.  
  
 [Pointeur de FExecuteInAppDomainCallback (fonction)](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 Obsolète. Pointe vers une fonction que le CLR appelle pour exécuter le code managé.  
  
 [Pointeur de FLockClrVersionCallback (fonction)](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 Obsolète. Pointe vers une fonction que le CLR appelle pour notifier l’hôte que l’initialisation a démarré ou s’est terminée.  
  
 [GetCLRIdentityManager (fonction)](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 Obsolète. Obtient un pointeur vers une interface qui permet au CLR de gérer les identités.  
  
 [LoadLibraryShim (fonction)](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 Obsolète. Charge une version spécifiée d’une DLL .NET Framework.  
  
 [LoadStringRC (fonction)](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 Obsolète. Traduit une valeur HRESULT dans un message d’erreur à l’aide de la culture par défaut du thread actuel.  
  
 [LoadStringRCEx (fonction)](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 Obsolète. Traduit une valeur HRESULT à un message d’erreur approprié pour la culture spécifiée.  
  
 [Pointeur de fonction LPOVERLAPPED_COMPLETION_ROUTINE](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 Obsolète. Pointe vers une fonction qui avertit l’hôte lorsqu’un chevauchement (autrement dit, asynchrone) e/s sur un périphérique est terminée.  
  
 [Pointeur de fonction LPTHREAD_START_ROUTINE](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 Obsolète. Pointe vers une fonction qui avertit l’hôte qu’un thread a commencé à s’exécuter.  
  
 [RunDll32ShimW (fonction)](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 Obsolète. Exécute la commande spécifiée.  
  
 [Pointeur de fonction WAITORTIMERCALLBACK](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 Obsolète. Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente a été signalé ou a expiré.  
  
## <a name="infrastructure-functions"></a>Fonctions d’infrastructure  
 Les fonctions de cette section sont utilisés par le .NET Framework.  
  
 [_CorDllMain (fonction)](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 Initialise le CLR recherche le point d’entrée managé dans l’en-tête CLR de l’assembly DLL et commence l’exécution.  
  
 [_CorExeMain (fonction)](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 Initialise le CLR recherche le point d’entrée managé dans l’en-tête CLR de l’assembly exécutable et commence l’exécution.  
  
 [_CorExeMain2 (fonction)](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 Exécute le point d’entrée dans le code mappé en mémoire spécifié. Cette fonction est appelée par le chargeur du système d’exploitation.  
  
 [_CorImageUnloading (fonction)](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 Notifie le chargeur lorsque les images de modules managés sont déchargées.  
  
 [_CorValidateImage (fonction)](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 Valide les images de modules managés et notifie le chargeur du système d’exploitation après avoir été chargés.  
  
## <a name="see-also"></a>Voir aussi  
 [.NET framework 4 hébergement fonctions statiques globales](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 
