---
title: "SOS.dll (Extension de d&#233;bogage SOS) | Microsoft Docs"
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
  - "déboguer des extensions"
  - "extensions de débogage SOS"
  - "SOS.dll"
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
caps.latest.revision: 55
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 55
---
# SOS.dll (Extension de d&#233;bogage SOS)
L’extension de débogage SOS (SOS.dll) vous aide à déboguer des programmes managés dans le débogueur Windows WinDbg.exe et dans Visual Studio en vous fournissant des informations sur l’environnement interne du CLR (Common Language Runtime). Cet outil requiert l'activation du débogage non managé pour votre projet. SOS.dll est installé automatiquement avec .NET Framework. Pour utiliser SOS.dll dans Visual Studio, vous devez installer le [Windows Driver Kit (WDK)](http://msdn.microsoft.com/windows/hardware/hh852362).  
  
> [!NOTE]
>  Si vous utilisez [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], SOS.dll est pris en charge dans le débogueur Windows au sein de Visual Studio, mais pas dans la fenêtre Exécution du débogueur Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
![command] [options]   
```  
  
## <a name="commands"></a>Commandes  
  
|Commande|Description|  
|-------------|-----------------|  
|**AnalyzeOOM** (**ao**)|Affiche les informations pour le dernier OOM qui s’est produit sur une demande d’allocation au tas de garbage collection. (Dans le garbage collection côté serveur, il affiche OOM, le cas échéant, sur chaque tas de garbage collection.)|  
|**BPMD** [**-nofuturemodule**] [*module name*> *method name*>] [**-md** <`MethodDesc`>] **-list** **-clear** \<*pending breakpoint number*> **-clearall**|Crée un point d'arrêt sur la méthode spécifiée dans le module spécifié.<br /><br /> Si le module et la méthode spécifiés n'ont pas été chargés, cette commande attend une notification indiquant que le module a été chargé et compilé juste-à-temps avant de créer un point d'arrêt.<br /><br /> Vous pouvez gérer la liste d’attente des points d’arrêt à l’aide de la **-liste**, **-effacer**, et **- clearall** options :<br /><br /> Le **-liste** option génère une liste de tous les points d’arrêt en attente. Si un point d'arrêt en attente a un ID de module non nul, ce point d'arrêt est spécifique à une fonction dans ce module spécifique chargé. Si le point d'arrêt en attente a un ID de module nul, ce point d'arrêt s'applique aux modules qui n'ont pas encore été chargés.<br /><br /> Utilisez le **-effacer** ou **- clearall** option de suppression en attente des points d’arrêt dans la liste.|  
|**CLRStack** [**-a**] [**-l**] [**-p**] [**-n**]|Fournit uniquement une trace de la pile du code managé.<br /><br /> Le **-p** option fournit les arguments à la fonction managée.<br /><br /> Le **-l** option affiche des informations sur les variables locales dans un frame. L’Extension de débogage SOS ne peut pas récupérer les noms locaux, la sortie pour les noms locaux est au format *adresse locale*> **=** \<*valeur*>.<br /><br /> Le **-**option (tous) est un raccourci pour **-l** et **-p**combinés.<br /><br /> Le **- n** option désactive l’affichage des noms de fichier source et les numéros de ligne. Si l'option SYMOPT_LOAD_LINES est spécifiée sur le débogueur, SOS recherche les symboles pour chaque frame managé et, s'il les trouve, affiche le nom de fichier source et le numéro de ligne correspondants. Le **- n** (aucun numéro de ligne) paramètre peut être spécifié pour désactiver ce comportement.<br /><br /> L’extension de débogage SOS n’affiche pas de frames de transition sur les plateformes x64 et IA-64.|  
|**COMState**|Répertorie le modèle cloisonné COM pour chaque thread et un pointeur `Context`, si disponible.|  
|**DumpArray** [**-start** \<*startIndex*>] [**-length** \<*length*>] [**-details**] [**-nofields**] *array object address*><br /><br /> ou<br /><br /> **DA** [**-start** \<*startIndex*>] [**-length** \<*length*>] [**-detail**] [**-nofields**] *array object address*>|Examine les éléments d'un objet tableau.<br /><br /> Le **-Démarrer** option spécifie l’index de départ à partir duquel afficher les éléments.<br /><br /> Le **-longueur** option spécifie le nombre d’éléments à afficher.<br /><br /> Le **-détails** option affiche les détails de l’élément à l’aide de la **DumpObj** et **DumpVC** formats.<br /><br /> Le **nofields -** option empêche l’affichage des tableaux. Cette option est disponible uniquement lorsque la **-détail** option est spécifiée.|  
|**DumpAssembly** \<*adresse d’assembly*>|Affiche des informations concernant un assembly.<br /><br /> Le **DumpAssembly** commande répertorie plusieurs modules, s’ils existent.<br /><br /> Vous pouvez obtenir une adresse d’assembly à l’aide de la **DumpDomain** commande.|  
|**DumpClass** \<*adresse EEClass*>|Affiche des informations sur la structure `EEClass` associée à un type.<br /><br /> Le **DumpClass** commande affiche les valeurs de champ statique mais n’affiche pas les valeurs de champ non statique.<br /><br /> Utilisez le **DumpMT**, **DumpObj**, **Name2EE**, ou **Token2EE** pour obtenir un `EEClass` adresse de structure.|  
|**DumpDomain** [*adresse du domaine*>]|Répertorie chaque <xref:System.Reflection.Assembly> de l’objet qui est chargé de la <xref:System.AppDomain> adresse d’objet.  Lorsqu’elle est appelée sans paramètres, la **DumpDomain** commande répertorie tous les <xref:System.AppDomain> objets dans un processus.|  
|**DumpHeap** [**-stat**] [**-strings**] [**-short**] [**-min** \<*size*>] [**-max** \<*size*>] [**-thinlock**] [**-startAtLowerBound**] [**-mt** \<*MethodTable address*>] [**-type** \<*partial type name*>][*start* [*end*]]|Affiche des informations sur le tas récupéré par le récupérateur de mémoire et des statistiques de collection concernant les objets.<br /><br /> Le **DumpHeap** commande affiche un avertissement si elle détecte une fragmentation excessive dans le tas de garbage collector.<br /><br /> Le **-stat** option restreint la sortie vers le résumé de type statistique.<br /><br /> Le **-chaînes** option limite la sortie à une valeur de chaîne type statistique.<br /><br /> Le **-court** option limite la sortie à l’adresse de chaque objet. Cela vous permet de canaliser facilement une sortie depuis la commande vers une autre commande de débogueur pour l'automation.<br /><br /> Le **-min** option ignore les objets inférieurs au `size` paramètre, spécifié en octets.<br /><br /> Le **-max** option ignore les objets supérieurs à la `size` paramètre, spécifié en octets.<br /><br /> Le **thinlock -** option indique ThinLocks.  Pour plus d’informations, consultez la **SyncBlk** commande.<br /><br /> L'option `-startAtLowerBound` force le parcours du segment de mémoire à commencer à la limite inférieure d'une plage d'adresses fournie. Pendant la phase de planification, le tas n'est pas souvent opérationnel parce que des objets sont déplacés. Cette option force **DumpHeap** à commencer son parcours à la limite inférieure spécifiée. Vous devez fournir l'adresse d'un objet valide comme limite inférieure pour que cette option fonctionne. Vous pouvez afficher la mémoire à l'adresse d'un mauvais objet pour rechercher manuellement la table de méthodes suivante. Si le garbage collection est actuellement en communication avec `memcopy`, vous pouvez également rechercher l'adresse de l'objet suivant en ajoutant la taille à l'adresse de démarrage, qui est fournie comme paramètre.<br /><br /> Le **- mt** option répertorie uniquement les objets qui correspondent aux spécifié `MethodTable` structure.<br /><br /> Le **-type** option répertorie uniquement les objets dont le nom type est une correspondance de sous-chaîne de la chaîne spécifiée.<br /><br /> Le paramètre `start` commence à répertorier les éléments à partir de l'adresse spécifiée.<br /><br /> Le paramètre `end` cesse de répertorier les éléments à l'adresse spécifiée.|  
|**DumpIL** \<*objet DynamicMethod managé*> |       *Pointeur DynamicMethodDesc*> |        *Pointeur MethodDesc*>|Affiche le Microsoft Intermediate Language (MSIL) associé à une méthode managée.<br /><br /> Notez que le langage MSIL dynamique est émis différemment du langage MSIL chargé à partir d'un assembly. Le langage MSIL dynamique fait référence aux objets d'un tableau d'objets managés plutôt qu'aux jetons de métadonnées.|  
|**DumpLog** [**-addr** \<*addressOfStressLog*>] [*Filenam*`e`>]|Écrit le contenu d'un journal de contrainte en mémoire dans le fichier spécifié. Si vous ne spécifiez pas de nom, cette commande crée un fichier appelé StressLog.txt dans le répertoire actif.<br /><br /> Le journal de contrainte en mémoire vous aide à diagnostiquer les échecs de contrainte sans utiliser de verrous ou d'E/S. Pour activer le journal de contrainte, définissez les clés de Registre suivantes sous HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework :<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> L'option `-addr` facultative vous permet de spécifier un journal de contrainte autre que le journal par défaut.|  
|**DumpMD** \<*adresse MethodDesc*>|Affiche des informations sur une structure `MethodDesc` à l'adresse spécifiée.<br /><br /> Vous pouvez utiliser la **IP2MD** pour obtenir le `MethodDesc` adresse d’une fonction managée de structure.|  
|**DumpMT** [**-MD**] *adresse MethodTable*>|Affiche des informations sur une table de méthodes à l'adresse spécifiée. Spécification de la **-MD** option affiche une liste de toutes les méthodes définies avec l’objet.<br /><br /> Chaque objet managé contient un pointeur de table de méthodes.|  
|**DumpMethodSig** \<*sigaddr*> *moduleadd*`r`>|Affiche des informations sur une structure `MethodSig` à l'adresse spécifiée.|  
|**DumpModule** [**- mt**] *adresse de Module*>|Affiche des informations sur un module à l'adresse spécifiée. Le **- mt** option affiche les types définis dans un module et les types référencés par le module<br /><br /> Vous pouvez utiliser la **DumpDomain** ou **DumpAssembly** commande pour récupérer l’adresse d’un module.|  
|**DumpObj** [**- nofields**] *adresse d’objet*><br /><br /> ou<br /><br /> **FAIRE** \<*adresse d’objet*>|Affiche des informations sur un objet à l'adresse spécifiée. Le **DumpObj** commande affiche les champs, les `EEClass` de la structure d’informations, la table de méthodes et la taille de l’objet.<br /><br /> Vous pouvez utiliser la **DumpStackObjects** commande pour récupérer l’adresse d’un objet.<br /><br /> Notez que vous pouvez exécuter la **DumpObj** commande dans les champs de type `CLASS` car ce sont des objets.<br /><br /> Le `-` **nofields** option empêche des champs de l’objet affiché, il est utile pour les objets comme chaîne.|  
|**DumpRuntimeTypes**|Affiche les objets de type au moment de l'exécution dans le tas de récupérateur de mémoire et répertorie leurs noms de types et tables de méthodes associés.|  
|**DumpStack** [**-EE**] [**-n**] [`top` *stack* [`bottom` *stac*`k`]]|Affiche une trace de la pile.<br /><br /> Le **- EE** option entraîne la **DumpStack** commande pour afficher uniquement les fonctions managées. Utilisez les paramètres `top` et `bottom` pour limiter les frames de pile affichés sur les plateformes x86.<br /><br /> Le **- n** option désactive l’affichage des noms de fichier source et les numéros de ligne. Si l'option SYMOPT_LOAD_LINES est spécifiée sur le débogueur, SOS recherche les symboles pour chaque frame managé et, s'il les trouve, affiche le nom de fichier source et le numéro de ligne correspondants. Le **- n** (aucun numéro de ligne) paramètre peut être spécifié pour désactiver ce comportement.<br /><br /> Sur les plates-formes x86 et x64, le **DumpStack** commande crée une trace de la pile détaillée.<br /><br /> Sur les plateformes IA-64, le **DumpStack** commande reproduit du débogueur **K** commande. Les paramètres `top` et `bottom` sont ignorés sur les plateformes IA-64.|  
|**DumpSig** \<*sigaddr*> *moduleaddr*>|Affiche des informations sur une structure `Sig` à l'adresse spécifiée.|  
|**DumpSigElem** \<*sigaddr*> *moduleaddr*>|Affiche un élément unique d'un objet de signature. Dans la plupart des cas, vous devez utiliser **DumpSig** d’examiner des objets de signature individuels. Toutefois, si une signature a été endommagée d’une certaine façon, vous pouvez utiliser **DumpSigElem** pour lire ses parties valides de celui-ci.|  
|**DumpStackObjects** [**-verify**] [`top` *stack* [`bottom` *stack*]]<br /><br /> ou<br /><br /> **DSO** [**-verify**] [`top` *stack* [`bottom` *stack*]]|Affiche tous les objets managés recherchés dans les limites de la pile actuelle.<br /><br /> Le **-Vérifiez** option valide chaque non statique `CLASS` champ d’un champ d’objet.<br /><br /> Utilisez le **DumpStackObject** commande avec les commandes de suivi de pile, telles que la **K** commande et le **CLRStack** commande pour déterminer les valeurs des variables locales et des paramètres.|  
|**DumpVC** \<*adresse MethodTable*> *adresse*>|Affiche des informations sur les champs d'une classe de valeur à l'adresse spécifiée.<br /><br /> Le **MethodTable** paramètre permet la **DumpVC** commande pour interpréter correctement les champs. Les classes de valeur ne disposent pas d'une table de méthodes comme premier champ.|  
|**EEHeap** [**-gc**] [**-loader**]|Affiche des informations sur la mémoire du processus consommée par les structures de données internes du Common Language Runtime.<br /><br /> Le **-gc** et **-chargeur** options limitent la sortie de cette commande vers les structures de données du garbage collector ou du chargeur.<br /><br /> Les informations pour le récupérateur de mémoire répertorient les plages de chaque segment dans le tas managé.  Si le pointeur se trouve dans une plage de segments spécifiée par **-gc**, le pointeur est un pointeur d’objet.|  
|**EEStack** [**-short**] [**-EE**]|Exécute le **DumpStack** commande sur tous les threads dans le processus.<br /><br /> Le **- EE** option est passée directement à la **DumpStack** commande. Le **-court** paramètre limite la sortie vers les types de threads suivants :<br /><br /> Threads avec un verrou.<br /><br /> Threads bloqués pour permettre un garbage collection.<br /><br /> Threads se trouvant actuellement dans le code managé.|  
|**EEVersion**|Affiche la version du Common Language Runtime.|  
|**EHInfo** [*adresse MethodDesc*>] [*Code adresse*>]|Affiche les blocs de gestion des exceptions dans une méthode spécifiée.  Cette commande affiche les adresses de code et les offsets du bloc de clause (bloc `try`) et du bloc de gestionnaire (bloc `catch`).|  
|**FAQ**|Affiche les questions fréquemment posées.|  
|**FinalizeQueue** [**-détail**] | [**-allReady**] [**-short**]|Affiche tous les objets enregistrés pour la finalisation.<br /><br /> Le **-détail** option affiche des informations supplémentaires concernant les `SyncBlocks` qui doivent être nettoyées et tous les `RuntimeCallableWrappers` (RCW) qui attendent de nettoyage. Ces deux structures de données sont mises en cache et nettoyées par le thread finaliseur lorsqu'il est exécuté.<br /><br /> L'option `-allReady` affiche tous les objets prêts pour la finalisation, qu'ils soient déjà marqués comme tel par le garbage collection ou qu'ils le soient par le garbage collection suivant. Les objets qui ne figurent pas dans la liste "prêt pour la finalisation" sont des objets finalisables qui ne sont plus associés à une racine. Cette option peut s'avérer très coûteuse, car elle vérifie si tous les objets des files d'attente finalisables sont toujours associés à une racine.<br /><br /> L'option `-short` limite la sortie à l'adresse de chaque objet. S’il est utilisé conjointement avec **- déjà**, il énumère tous les objets qui ont un finaliseur qui n’est plus enracinés. S'il est utilisé indépendamment, il répertorie tous les objets dans les files d'attente finalisables et "prêtes pour la finalisation".|  
|**FindAppDomain** \<*adresse d’objet*>|Détermine le domaine d'application d'un objet à l'adresse spécifiée.|  
|**FindRoots** **-gen** \<*N*> | **-gen any** |* adresse de l’objet*>|Provoque l’arrêt du débogueur dans l’élément débogué sur la collection suivante de la génération spécifiée. L'effet est réinitialisé dès que l'arrêt se produit. Pour arrêter la collection suivante, vous devez rééditer la commande. Le * <object></object> \> * cette commande est utilisée après l’arrêt provoqué par le **-gen** ou **-la génération d’un** s’est produite. À ce stade, le programme débogué est dans l’état de **FindRoots** identifie des racines pour les objets à partir de l’actuel des générations condamnées.|  
|**GCHandles** [**- perdomain**]|Affiche des statistiques sur les handles du récupérateur de mémoire dans le processus.<br /><br /> Le **perdomain -** option organise les statistiques par domaine d’application.<br /><br /> Utilisez le **GCHandles** commande pour rechercher les fuites de mémoire provoquées par les fuites du handle du garbage collector. Par exemple, une fuite de mémoire se produit lorsque le code conserve un grand tableau, car un handle fort du récupérateur de mémoire pointe encore sur ce dernier ; le handle est ignoré sans libérer le tableau.|  
|**GCHandleLeaks**|Recherche dans la mémoire des références à des handles forts et épinglés du récupérateur de mémoire dans le processus et affiche les résultats. Si un handle est trouvé, le **GCHandleLeaks** commande affiche l’adresse de la référence. Si aucun handle n'est trouvé dans la mémoire, cette commande affiche une notification.|  
|**GCInfo** \<*adresse MethodDesc*>\<*adresse de Code*>|Affiche les données spécifiant les registres ou les emplacements de pile contenant des objets managés. Si un garbage collection a lieu, le collector doit connaître les emplacements des références aux objets pour pouvoir les mettre à jour avec les nouvelles valeurs de pointeur d’objet.|  
|**GCRoot** [**- nostacks**] *adresse d’objet*>|Affiche des informations sur les références (ou racines) à un objet à l'adresse spécifiée.<br /><br /> Le **GCRoot** commande examine le tas managé tout entier et la table de handles pour les handles d’autres objets et les handles de la pile. Une recherche des pointeurs vers les objets est ensuite réalisée dans chaque pile et dans la file d'attente du finaliseur.<br /><br /> Cette commande ne détermine pas si la racine d'une pile est valide ou ignorée. Utilisez le **CLRStack** et **U** commandes pour désassembler le frame auquel appartient la valeur locale ou d’argument afin de déterminer si la racine de la pile est en cours d’utilisation.<br /><br /> Le **nostacks -** option restreint la recherche aux handles du garbage collector et aux objets.|  
|**GCWhere**  *<object></object>\>*|Affiche l’emplacement et la taille dans le tas de garbage collection de l’argument passé. Lorsque l’argument se trouve dans le tas managé, mais n’est pas une adresse d’objet valide, la taille s’affiche en tant que 0 (zéro).|  
|**help** [*command*>] [`faq`]|Affiche toutes les commandes disponibles lorsque aucun paramètre n'est spécifié ou affiche des informations d'aide détaillées sur la commande spécifiée.<br /><br /> Le paramètre `faq` affiche les réponses aux questions fréquentes.|  
|**HeapStat** [**inclUnrooted -** | **-iu**]|Affiche les tailles de génération pour chaque tas et l'espace libre total dans chaque génération sur chaque tas. Si-**inclUnrooted** est spécifiée, le rapport inclut des informations sur les objets managés du tas de garbage collection qui n’est plus enraciné.|  
|**HistClear**|Libère toutes les ressources utilisées par la famille de commandes `Hist`.<br /><br /> En général, vous n'avez pas à appeler `HistClear`explicitement, parce que chaque `HistInit` nettoie les ressources précédentes.|  
|**HistInit**|Initialise les structures SOS du journal de contrainte enregistré dans l’élément débogué.|  
|**HistObj***<obj_address>*</obj_address>|Examine tous les enregistrements de réadressage du journal de contrainte et affiche la chaîne des réadressages de garbage collection qui ont pu mener à l’adresse passée comme un argument.|  
|**HistObjFind**  *<obj_address>*</obj_address>|Affiche toutes les entrées de journal qui référencent un objet à l'adresse spécifiée.|  
|**HistRoot***<>\>*|Affiche les informations liées aux promotions et aux réadressages de la racine spécifiée.<br /><br /> La valeur racine peut être utilisée pour suivre le déplacement d’un objet dans les garbage collections.|  
|**IP2MD** \<*adresse de Code*>|Affiche la structure `MethodDesc` à l'adresse spécifiée dans le code compilé juste-à-temps (JIT).|  
|`ListNearObj`(`lno`)*<obj_address>*</obj_address>|Affiche les objets précédant et suivant l'adresse spécifiée. La commande recherche dans le tas de garbage collection l’adresse qui ressemble à un début valide d’objet managé (selon une table de méthodes valide), ainsi que l’objet qui suit l’adresse d’argument.|  
|**MinidumpMode** [**0**] [**1**]|Empêche l'exécution de commandes potentiellement dangereuses lors de l'utilisation d'un minidump.<br /><br /> Transmettez **0** pour désactiver cette fonctionnalité ou **1** pour activer cette fonctionnalité. Par défaut, le **MinidumpMode** a la valeur **0**.<br /><br /> Les minidumps créés avec la **.dump /m** commande ou **.dump** commande ont des données spécifiques au CLR limitées et vous permettent d’exécuter correctement uniquement un sous-ensemble de commandes SOS. Certaines commandes peuvent échouer avec des erreurs inattendues, car des zones de mémoire requises ne sont pas mappées ou ne sont mappées que partiellement. Cette option vous empêche d'exécuter des commandes potentiellement dangereuses dans les minidumps.|  
|**Name2EE** \<*nom du module*> *nom du type ou de méthode*><br /><br /> ou<br /><br /> **Name2EE** \<*module name*>**!** \< *nom de type ou de méthode*>|Affiche la structure `MethodTable` et la structure `EEClass` pour le type ou la méthode spécifié dans le module spécifié.<br /><br /> Le module spécifié doit être chargé dans le processus.<br /><br /> Pour obtenir le nom de type correct, parcourez le module à l’aide de la [Ildasm.exe (désassembleur IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). Vous pouvez également passer `*` en tant que paramètre de nom de module pour rechercher tous les modules managés chargés. Le *nom du module* paramètre peut également être le nom du débogueur pour un module, tel que `mscorlib` ou `image00400000`.<br /><br /> Cette commande prend en charge la syntaxe du débogueur Windows `module` > `!` < `type`>. Le type doit être qualifié complet.|  
|**ObjSize** [*adresse d’objet*>] | [**-aggregate**] [**-stat**]|Affiche la taille de l'objet spécifié. Si vous ne spécifiez pas de paramètres, le **ObjSize** commande affiche la taille de tous les objets trouvés dans les threads managés, affiche tous les handles du garbage collector dans le processus et additionne la taille de tous les objets pointés par ces handles. Le **ObjSize** commande inclut la taille de tous les objets enfants en plus du parent.<br /><br /> Le **-agrégation** option peut être utilisée conjointement avec la **-stat** argument pour obtenir une vue détaillée des types qui sont encore associés à une racine. À l’aide de **! dumpheap-stat** et **! objsize-aggregate - stat**, vous pouvez déterminer quels objets ne sont plus enracinés et diagnostiquer différents problèmes de mémoire.|  
|**PrintException** [**-imbriquée**] [**-lignes**] [*adresse d’objet Exception*>]<br /><br /> ou<br /><br /> **PE** [**-imbriquée**] [*adresse d’objet Exception*>]|Affiche et met en forme les champs de n’importe quel objet dérivé de la <xref:System.Exception> classe à l’adresse spécifiée. Si vous ne spécifiez pas d’adresse, le **PrintException** commande affiche la dernière exception levée dans le thread actuel.<br /><br /> Le **-imbriquée** option affiche des détails sur les objets d’exception imbriquée.<br /><br /> Le **-lignes** option affiche des informations sur la source, si elle est disponible.<br /><br /> Vous pouvez utiliser cette commande pour mettre en forme et consulter le champ `_stackTrace` qui est un tableau binaire.|  
|**ProcInfo** [**-env**] [**-time**] [**-mem**]|Affiche les variables d'environnement pour le processus, le temps CPU noyau et les statistiques relatives à l'utilisation de la mémoire.|  
|**RCWCleanupList** \<*adresse RCWCleanupList*>|Affiche la liste des wrappers RCW (Runtime Callable Wrapper) à l'adresse spécifiée qui sont en attente de nettoyage.|  
|**SaveModule** \<*adresse de Base*> *nom de fichier*>|Écrit une image, chargée dans la mémoire à l'adresse spécifiée, dans le fichier spécifié.|  
|**SOSFlush**|Vide un cache SOS interne.|  
|**StopOnException** [**-dérivés**] [**-créer** | **-rapide2**] *Exception*> *numéro de Registre pseudo-élément*>|Entraîne l'arrêt du débogueur lorsque l'exception spécifiée est levée, mais la poursuite de son exécution lorsque d'autres exceptions sont levées.<br /><br /> Le **-dérivée** option intercepte l’exception spécifiée, ainsi que chaque exception dérivée de l’exception spécifiée.|  
|**SyncBlk** [**-all** | *numéro syncblk*>]|Affiche la structure `SyncBlock` spécifiée ou l'ensemble des structures `SyncBlock`.  Si vous ne passez pas d’arguments, les **SyncBlk** commande affiche le `SyncBlock` structure correspondant aux objets possédés par un thread.<br /><br /> Une structure `SyncBlock` est un conteneur pour les informations supplémentaires qui n'a pas besoin d'être créé pour chaque objet. Elle peut contenir des données COM Interop, des codes de hachage et des informations de verrouillage pour les opérations thread-safe.|  
|**Pool de threads**|Affiche des informations sur le pool de threads managé, y compris le nombre de demandes de tâches dans la file d'attente, le nombre de threads de port de terminaison, et le nombre de minuteries.|  
|**Token2EE** \<*nom du module*> *jetons*>|Convertit le jeton de métadonnées spécifié dans le module spécifié en structure `MethodTable` ou `MethodDesc`.<br /><br /> Vous pouvez passer `*` comme paramètre de nom de module pour rechercher le mappage de ce jeton dans chaque module managé chargé. Vous pouvez également passer le nom du débogueur pour un module, tel que `mscorlib` ou `image00400000`.|  
|**Threads** [**-live**] [**-special**]|Affiche tous les threads managés dans le processus.<br /><br /> Le **Threads** commande affiche le débogueur ID abrégé, l’ID de thread de common language runtime et l’ID de thread de système d’exploitation.  En outre, les **Threads** commande affiche une colonne domaine qui indique le domaine d’application dans lequel un thread s’exécute, une colonne APT qui affiche le mode apartment COM et une colonne Exception qui affiche la dernière exception levée dans le thread.<br /><br /> Le **-live** option affiche les threads associés à un thread actif.<br /><br /> Le **-spéciale** option affiche tous les threads spéciaux créés par le CLR. Les threads spéciaux incluent les threads de garbage collection (dans le garbage collection simultané et serveur), les threads d’assistance du débogueur, les threads finaliseurs, <xref:System.AppDomain> décharger les threads et les threads de minuterie ThreadPool.|  
|**Des États du thread ** *champ de valeur d’état***>**|Affiche l'état du thread. Le `value` paramètre est la valeur de la `State` de la **Threads** génération de rapports.<br /><br /> Exemple :<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|  
|**TraverseHeap** [**- xml**] *nom de fichier*>|Écrit les informations du tas dans le fichier spécifié dans un format compris par le profileur du CLR. Le **- xml** option entraîne la **TraverseHeap** commande pour mettre en forme le fichier au format XML.<br /><br /> Vous pouvez télécharger le profileur CLR à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=67325).|  
|**U** [**-gcinfo**] [**-ehinfo**] [**-n**] *MethodDesc address*> | *Code adresse*>|Affiche un code machine annoté d'une méthode managée spécifié par un pointeur de structure `MethodDesc` pour la méthode ou par une adresse de code dans le corps de la méthode. Le **U** commande affiche l’intégralité de la méthode du début à la fin, avec les annotations qui convertissent les jetons de métadonnées en noms.<br /><br /> Le **- gcinfo** option entraîne la **U** pour afficher les `GCInfo` structure pour la méthode.<br /><br /> Le **- ehinfo** option affiche des informations sur les exceptions pour la méthode. Vous pouvez également obtenir ces informations avec la **EHInfo** commande.<br /><br /> Le **- n** option désactive l’affichage des noms de fichier source et les numéros de ligne. Si l'option SYMOPT_LOAD_LINES est spécifiée sur le débogueur, SOS recherche les symboles pour chaque frame managé et, s'il les trouve, affiche le nom de fichier source et le numéro de ligne correspondants. Vous pouvez spécifier le **- n** option pour désactiver ce comportement.|  
|**VerifyHeap**|Vérifie le tas de récupérateur de mémoire pour rechercher des signes d'altération et affiche toutes les erreurs trouvées.<br /><br /> Les altérations du tas peuvent être provoquées par des appels de code construits de manière incorrecte.|  
|**VerifyObj** \<*adresse d’objet*>|Vérifie l’objet passé comme argument à la recherche de signes d’altération.|  
|**VMMap**|Parcourt l'espace d'adressage virtuel et affiche le type de protection appliqué à chaque région.|  
|**VMStat**|Fournit un résumé de l’espace d’adressage virtuel, classé par type de protection appliqué à cette mémoire (libre, réservé, validé, privé, mappé, image). La colonne TOTAL affiche le résultat de la colonne MOYENNE multipliée par la colonne COMPTE BLQ.|  
  
## <a name="remarks"></a>Notes  
 L’extension de débogage SOS vous permet d’afficher des informations sur l’exécution du code au sein du Common Language Runtime. Par exemple, vous pouvez utiliser l’extension de débogage SOS pour afficher des informations sur le tas managé, rechercher des altérations du tas, afficher les types de données internes utilisés par le runtime et afficher des informations sur l’ensemble du code managé exécuté au sein du runtime.  
  
 Pour utiliser l’Extension de débogage SOS dans Visual Studio, vous devez installer le [Windows Driver Kit (WDK)](http://msdn.microsoft.com/windows/hardware/hh852362). Pour plus d’informations sur l’environnement de débogage intégré dans Visual Studio, consultez [environnements de débogage](http://msdn.microsoft.com/library/windows/hardware/hh406268.aspx) dans le centre de développement Windows.  
  
 Vous pouvez également utiliser l’Extension de débogage SOS en la chargeant dans le débogueur WinDbg.exe, qui est disponible à partir de la [site Web WDK and Developer Tools](http://go.microsoft.com/fwlink/?LinkId=103787)et l’exécution de commandes dans WinDbg.exe.  
  
 Pour charger l’Extension de débogage SOS dans le débogueur WinDbg.exe, exécutez la commande suivante dans l’outil :  
  
```  
.loadby sos clr  
```  
  
 WinDbg.exe et Visual Studio utilisent une version de SOS.dll qui correspond à la version de Mscorwks.dll actuellement utilisée. Dans les versions 1.1 et 2.0 du .NET Framework, SOS.dll est installé dans le même répertoire que Mscorwks.dll. Par défaut, vous devez utiliser la version de SOS.dll qui correspond à la version actuelle de Mscorwks.dll.  
  
 Pour utiliser un fichier dump créé sur un autre ordinateur, vérifiez que le fichier Mscorwks.dll fourni avec cette installation se trouve dans votre chemin d'accès aux symboles, et chargez la version correspondante de SOS.dll.  
  
 Pour charger une version spécifique de SOS.dll, tapez la commande suivante dans le débogueur Windows :  
  
```  
.load <full path to sos.dll>  
```  
  
## <a name="examples"></a>Exemples  
 La commande suivante affiche le contenu d'un tableau à l'adresse `00ad28d0`.  L'affichage démarre à partir du deuxième élément et se poursuit avec les cinq éléments suivants.  
  
```  
!dumparray -start 2 -length 5 -detail 00ad28d0   
```  
  
 La commande suivante affiche le contenu d'un assembly à l'adresse `1ca248`.  
  
```  
!dumpassembly 1ca248  
```  
  
 La commande suivante affiche des informations sur le tas de récupérateur de mémoire.  
  
```  
!dumpheap  
```  
  
 La commande suivante écrit le contenu du journal de contrainte en mémoire dans un fichier appelé StressLog.txt (par défaut) dans le répertoire actif.  
  
```  
!DumpLog  
```  
  
 La commande suivante affiche la structure `MethodDesc` à l'adresse `902f40`.  
  
```  
!dumpmd 902f40  
```  
  
 La commande suivante affiche des informations sur un module à l'adresse `1caa50`.  
  
```  
!dumpmodule 1caa50  
```  
  
 La commande suivante affiche des informations sur un objet à l'adresse `a79d40`.  
  
```  
!DumpObj a79d40  
```  
  
 La commande suivante affiche les champs d'une classe de valeur à l'adresse `00a79d9c`, à l'aide de la table de méthodes à l'adresse `0090320c`.  
  
```  
!DumpVC 0090320c 00a79d9c  
```  
  
 La commande suivante affiche la mémoire du processus utilisée par le récupérateur de mémoire.  
  
```  
!eeheap -gc  
```  
  
 La commande suivante affiche tous les objets planifiés pour la finalisation.  
  
```  
!finalizequeue  
```  
  
 La commande suivante détermine le domaine d'application d'un objet à l'adresse `00a79d98`.  
  
```  
!findappdomain 00a79d98  
```  
  
 La commande suivante affiche tous les handles du récupérateur de mémoire dans le processus actuel.  
  
```  
!gcinfo 5b68dbb8   
```  
  
 La commande suivante affiche les structures `MethodTable` et `EEClass` pour la méthode `Main`, dans la classe `MainClass`, dans le module `unittest.exe`.  
  
```  
!name2ee unittest.exe MainClass.Main  
```  
  
 La commande suivante affiche des informations sur le jeton de métadonnées à l'adresse `02000003` dans le module `unittest.exe`.  
  
```  
!token2ee unittest.exe 02000003  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Outils](../../../docs/framework/tools/index.md)   
 [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md)