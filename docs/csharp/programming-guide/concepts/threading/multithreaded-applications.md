---
title: Applications multithread (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: b7015cfb-d506-4eac-b2f8-b2caaa9cc977
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: dfe0f9c6e911295270df8464d1070a524412466d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="multithreaded-applications-c"></a>Applications multithread (C#)
Avec C#, vous pouvez écrire des applications qui effectuent plusieurs tâches en même temps. Les tâches présentant le risque d’accaparer les ressources d’autres tâches peuvent s’exécuter sur des threads distincts : ce processus est appelé *multithreading* ou *threading libre*.  
  
 Les applications qui utilisent le multithreading sont plus réactives aux entrées utilisateur, car l’interface utilisateur reste active pendant que les tâches sollicitant beaucoup le processeur s’exécutent sur des threads distincts. Le multithreading est également utile quand vous créez des applications scalables, car vous pouvez ajouter des threads au fil de l’augmentation de la charge de travail.  
  
## <a name="creating-and-using-threads"></a>Création et utilisation des threads  
 Si vous avez besoin plus de contrôle sur le comportement des threads de votre application, vous pouvez gérer vous-même les threads. Notez cependant que l’écriture d’applications multithreads correctes peut être difficile : votre application peut cesser de répondre ou rencontrer des erreurs transitoires dues aux conditions de concurrence. Pour plus d’informations, consultez [Composants thread-safe](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).  
  
 Pour créer un thread, vous devez déclarer une variable de type <xref:System.Threading.Thread> et appeler le constructeur, en fournissant le nom de la procédure ou de la méthode que vous voulez exécuter sur le nouveau thread. Le code suivant fournit un exemple.  
  
```csharp  
System.Threading.Thread newThread =  
    new System.Threading.Thread(AMethod);  
```  
  
### <a name="starting-and-stopping-threads"></a>Démarrage et arrêt des threads  
 Pour lancer l’exécution d’un nouveau thread, utilisez la méthode <xref:System.Threading.Thread.Start%2A>, comme dans le code suivant.  
  
```csharp  
newThread.Start();  
```  
  
 Pour arrêter l’exécution d’un thread, utilisez la méthode <xref:System.Threading.Thread.Abort%2A>, comme dans le code suivant.  
  
```csharp  
newThread.Abort();  
```  
  
 En plus de démarrer et d’arrêter les threads, vous pouvez aussi les suspendre en appelant la méthode <xref:System.Threading.Thread.Sleep%2A> ou <xref:System.Threading.Thread.Suspend%2A>, reprendre un thread suspendu à l’aide de la méthode <xref:System.Threading.Thread.Resume%2A> et détruire un thread à l’aide de la méthode <xref:System.Threading.Thread.Abort%2A>.  
  
### <a name="thread-methods"></a>Méthodes pour les threads  
 Le tableau suivant répertorie certaines des méthodes que vous pouvez utiliser pour contrôler des threads individuels.  
  
|Méthode|Action|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|Démarre l’exécution d’un thread.|  
|<xref:System.Threading.Thread.Sleep%2A>|Suspend un thread pendant une durée spécifiée.|  
|<xref:System.Threading.Thread.Suspend%2A>|Suspend un thread quand celui-ci atteint un point sécurisé.|  
|<xref:System.Threading.Thread.Abort%2A>|Arrête un thread quand celui-ci atteint un point sécurisé.|  
|<xref:System.Threading.Thread.Resume%2A>|Redémarre un thread suspendu.|  
|<xref:System.Threading.Thread.Join%2A>|Force le thread actif à attendre qu’un autre thread se termine. Si elle est utilisée avec une valeur de délai d’attente, cette méthode retourne `True` si le thread se termine dans le délai imparti.|  
  
### <a name="safe-points"></a>Points sécurisés  
 L’action de la plupart de ces méthodes est explicite, mais le concept de *points sécurisés* est peut être nouveau pour vous. Les points sécurisés sont des endroits dans le code où le common language runtime peut effectuer sans risque une opération de *garbage collection*, qui est le processus consistant à libérer les variables inutilisées et à libérer la mémoire. Quand vous appelez la méthode <xref:System.Threading.Thread.Abort%2A> ou <xref:System.Threading.Thread.Suspend%2A> d’un thread, le common language runtime analyse le code et détermine l’emplacement approprié pour arrêter l’exécution d’un thread.  
  
### <a name="thread-properties"></a>Propriétés du thread  
 Les threads contiennent également plusieurs propriétés utiles, qui sont répertoriées dans le tableau suivant :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Contient la valeur `True` si un thread est actif.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Obtient ou définit une valeur booléenne qui indique si un thread est ou doit être un thread d’arrière-plan. Les threads d’arrière-plan ressemblent aux threads de premier plan, excepté qu’un thread d’arrière-plan n’empêche pas un processus de s’arrêter. Une fois que tous les threads de premier plan appartenant à un processus sont arrêtés, le common language runtime met fin au processus en appelant la méthode <xref:System.Threading.Thread.Abort%2A> sur les threads d’arrière-plan encore actifs.|  
|<xref:System.Threading.Thread.Name%2A>|Obtient ou définit le nom d’un thread. Généralement utilisé pour découvrir des threads individuels lors du débogage.|  
|<xref:System.Threading.Thread.Priority%2A>|Obtient ou définit une valeur qui est utilisée par le système d’exploitation pour classer par priorité la planification des threads.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Contient une valeur qui décrit le ou les états d’un thread.|  
  
## <a name="thread-priorities"></a>Priorités des threads  
 Chaque thread a une propriété priority, qui détermine la taille d’un intervalle de temps processeur pendant lequel il doit s’exécuter. Le système d’exploitation alloue des intervalles de temps plus longs aux threads à priorité élevée, et des intervalles de temps plus courts pour les threads de priorité basse. Les nouveaux threads sont créés avec la valeur `Normal`, mais vous pouvez remplacer la valeur de la propriété <xref:System.Threading.Thread.Priority%2A> par n’importe quelle valeur contenue dans l’énumération <xref:System.Threading.ThreadPriority>.  
  
 Consultez <xref:System.Threading.ThreadPriority> pour obtenir une description détaillée des différentes priorités de thread.  
  
## <a name="foreground-and-background-threads"></a>Threads de premier plan et d'arrière-plan  
 Un *thread de premier plan* peut s’exécuter indéfiniment, tandis qu’un *thread d’arrière-plan* s’arrête dès que le dernier thread de premier plan s’est arrêté. Vous pouvez utiliser la propriété <xref:System.Threading.Thread.IsBackground%2A> pour déterminer ou modifier l’état d’arrière-plan d’un thread.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Thread>   
 [Synchronisation des threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)   
 [Paramètres et valeurs de retour pour les procédures multithread (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)   
 [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)

