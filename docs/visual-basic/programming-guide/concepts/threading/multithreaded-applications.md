---
title: Les Applications multithread (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 02b0444b-2e68-4f2c-bc28-28c046004017
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5bde7f49a2f2bc8a2e6c1eeab3722428b8a37a95
ms.lasthandoff: 03/13/2017

---
# <a name="multithreaded-applications-visual-basic"></a>Applications multithread (Visual Basic)
Avec Visual Basic, vous pouvez écrire des applications qui effectuent plusieurs tâches en même temps. Tâches avec le risque d’autres tâches peuvent être effectuées sur des threads séparés, un processus appelé *multithreading* ou *libre de thread*.  
  
 Les applications qui utilisent le multithreading plus réactives aux entrées d’utilisateur, car l’interface utilisateur reste active pendant que les tâches sollicitant beaucoup le processeur s’exécutent sur des threads séparent. Le multithreading est également utile lorsque vous créez des applications évolutives, car vous pouvez ajouter des threads en tant que la charge de travail augmente.  
  
## <a name="creating-and-using-threads"></a>Création et utilisation de Threads  
 Si vous avez besoin de davantage de contrôle sur le comportement des threads de votre application, vous pouvez gérer vous-même les threads. Toutefois, notez que l’écriture d’applications multithreads correctes peut être difficile : votre application peut cesser de répondre ou rencontrer des erreurs transitoires dues aux conditions de concurrence. Pour plus d’informations, consultez [composants Thread-Safe](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).  
  
 Vous créez un nouveau thread en déclarant une variable de type <xref:System.Threading.Thread>et appeler le constructeur, en fournissant le nom de la procédure ou la méthode que vous souhaitez exécuter sur le nouveau thread.</xref:System.Threading.Thread> Le code suivant fournit un exemple.  
  
```vb  
Dim newThread As New System.Threading.Thread(AddressOf AMethod)  
```  
  
### <a name="starting-and-stopping-threads"></a>Démarrage et arrêt des Threads  
 Pour démarrer l’exécution d’un nouveau thread, utilisez la <xref:System.Threading.Thread.Start%2A>méthode, comme indiqué dans le code suivant.</xref:System.Threading.Thread.Start%2A>  
  
```vb  
newThread.Start()  
```  
  
 Pour arrêter l’exécution d’un thread, utilisez la <xref:System.Threading.Thread.Abort%2A>méthode, comme indiqué dans le code suivant.</xref:System.Threading.Thread.Abort%2A>  
  
```vb  
newThread.Abort()  
```  
  
 Non seulement démarrer et arrêter des threads, vous pouvez également suspendre des threads en appelant le <xref:System.Threading.Thread.Sleep%2A>ou <xref:System.Threading.Thread.Suspend%2A>(méthode), redémarrer un thread suspendu à l’aide de la <xref:System.Threading.Thread.Resume%2A>(méthode) et détruire un thread à l’aide de la <xref:System.Threading.Thread.Abort%2A>méthode</xref:System.Threading.Thread.Abort%2A> </xref:System.Threading.Thread.Resume%2A> </xref:System.Threading.Thread.Suspend%2A> </xref:System.Threading.Thread.Sleep%2A>  
  
### <a name="thread-methods"></a>Méthodes de thread  
 Le tableau suivant répertorie certaines des méthodes que vous pouvez utiliser pour contrôler les threads individuels.  
  
|Méthode|Action|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A></xref:System.Threading.Thread.Start%2A>|Entraîne un thread commencent à s’exécuter.|  
|<xref:System.Threading.Thread.Sleep%2A></xref:System.Threading.Thread.Sleep%2A>|Suspend un thread pendant une durée spécifiée.|  
|<xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Suspend%2A>|Suspend un thread lorsque celui-ci atteint un point sûr.|  
|<xref:System.Threading.Thread.Abort%2A></xref:System.Threading.Thread.Abort%2A>|Interrompt un thread lorsque celui-ci atteint un point sûr.|  
|<xref:System.Threading.Thread.Resume%2A></xref:System.Threading.Thread.Resume%2A>|Redémarre un thread suspendu|  
|<xref:System.Threading.Thread.Join%2A></xref:System.Threading.Thread.Join%2A>|Oblige le thread actuel attendre la fin d’un autre thread. Si utilisé avec une valeur de délai d’attente, cette méthode retourne `True` si le thread se termine dans le délai imparti.|  
  
### <a name="safe-points"></a>Points sans risque  
 La plupart de ces méthodes est explicite, mais le concept de *points sans risque* peut être nouveau pour vous. Points sûrs sont des emplacements de code où le common language runtime pour effectuer automatique *le garbage collection*, le processus de libérer des variables inutilisées et de libération de la mémoire. Lorsque vous appelez le <xref:System.Threading.Thread.Abort%2A>ou <xref:System.Threading.Thread.Suspend%2A>(méthode) d’un thread, le common language runtime analyse le code et détermine l’emplacement d’un emplacement approprié pour l’arrêt du thread.</xref:System.Threading.Thread.Suspend%2A> </xref:System.Threading.Thread.Abort%2A>  
  
### <a name="thread-properties"></a>Propriétés du thread  
 Les threads contiennent également plusieurs propriétés utiles, comme indiqué dans le tableau suivant :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A></xref:System.Threading.Thread.IsAlive%2A>|Contient la valeur `True` si un thread est actif.|  
|<xref:System.Threading.Thread.IsBackground%2A></xref:System.Threading.Thread.IsBackground%2A>|Obtient ou définit une valeur booléenne qui indique si un thread est ou doit être un thread d’arrière-plan. Threads d’arrière-plan ressemblent aux threads de premier plan, mais un thread d’arrière-plan n’empêche pas un processus s’arrête. Une fois que tous les threads de premier plan appartenant à un processus sont arrêtés, le common language runtime termine le processus en appelant le <xref:System.Threading.Thread.Abort%2A>méthode sur les threads d’arrière-plan restés actifs.</xref:System.Threading.Thread.Abort%2A>|  
|<xref:System.Threading.Thread.Name%2A></xref:System.Threading.Thread.Name%2A>|Obtient ou définit le nom d’un thread. Généralement utilisé pour découvrir des threads individuels lors du débogage.|  
|<xref:System.Threading.Thread.Priority%2A></xref:System.Threading.Thread.Priority%2A>|Obtient ou définit une valeur qui est utilisée par le système d’exploitation pour classer par priorité de planification des threads.|  
|<xref:System.Threading.Thread.ThreadState%2A></xref:System.Threading.Thread.ThreadState%2A>|Contient une valeur qui décrit l’état ou des États d’un thread.|  
  
## <a name="thread-priorities"></a>Les priorités de thread  
 Chaque thread a une propriété priority, qui détermine comment grande ou petite une tranche de temps processeur à exécuter. Le système d’exploitation alloue des tranches de temps plus longs à des threads hautement prioritaires et les tranches de temps plus courts pour les threads de priorité basse. Nouveaux threads sont créés avec la valeur de `Normal`, mais vous pouvez modifier le <xref:System.Threading.Thread.Priority%2A>propriété à n’importe quelle valeur dans la <xref:System.Threading.ThreadPriority>énumération.</xref:System.Threading.ThreadPriority> </xref:System.Threading.Thread.Priority%2A>  
  
 Consultez <xref:System.Threading.ThreadPriority>pour obtenir une description détaillée des différentes priorités des threads.</xref:System.Threading.ThreadPriority>  
  
## <a name="foreground-and-background-threads"></a>Threads de premier plan et d'arrière-plan  
 A *thread de premier plan* peut s’exécuter indéfiniment, tandis qu’un *thread d’arrière-plan* s’arrête dès que le dernier thread de premier plan s’est arrêté. Vous pouvez utiliser le <xref:System.Threading.Thread.IsBackground%2A>propriété pour déterminer ou changer l’état d’un thread d’arrière-plan.</xref:System.Threading.Thread.IsBackground%2A>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Thread></xref:System.Threading.Thread>   
 [Synchronisation de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)   
 [Paramètres et valeurs de retour pour les procédures multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)   
 [Threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)
