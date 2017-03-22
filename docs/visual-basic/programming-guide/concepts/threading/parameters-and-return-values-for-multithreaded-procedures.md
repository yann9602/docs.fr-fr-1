---
title: "Paramètres et valeurs de retour pour les procédures multithread (Visual Basic) | Documents Microsoft"
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
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5d8adde531d31aa6bf353f53bd4cfecc084f515
ms.lasthandoff: 03/13/2017

---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>Paramètres et valeurs de retour pour les procédures multithread (Visual Basic)
Apport et le retour des valeurs dans une application multithread sont complexe, car le constructeur de la classe thread doit être passé à une procédure qui n’accepte aucun argument et ne retourne aucune valeur. Les sections suivantes montrent quelques méthodes simples pour fournir des paramètres et valeurs de retour à partir de procédures sur des threads séparés.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Fournir des paramètres pour les procédures multithread  
 La meilleure façon de fournir des paramètres pour un appel de méthode multithread consiste à placer la méthode cible dans une classe et à définir les champs de cette classe qui fera office de paramètres pour le nouveau thread. L’avantage de cette approche est que vous pouvez créer une nouvelle instance de la classe, avec ses propres paramètres, chaque fois que vous souhaitez démarrer un nouveau thread. Par exemple, supposons que vous avez une fonction qui calcule la surface d’un triangle, comme dans le code suivant :  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 Vous pouvez écrire une classe qui encapsule la `CalcArea` la fonction et crée des champs pour stocker les paramètres d’entrée, comme suit :  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 Pour utiliser le `AreaClass`, vous pouvez créer un `AreaClass` et définissez la `Base` et `Height` propriétés comme indiqué dans le code suivant :  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 Notez que la `TestArea` procédure ne vérifie pas la valeur de la `Area` champ après avoir appelé la `CalcArea` méthode. Étant donné que `CalcArea` s’exécute sur un thread séparé, le `Area` n’est pas garanti que le champ si vous le vérifiez immédiatement après avoir appelé `Thread.Start`. La section suivante indique une meilleure méthode pour retourner des valeurs à partir de procédures multithreads.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Retour de valeurs à partir de procédures multithreads  
 Retour de valeurs à partir de procédures qui s’exécutent sur des threads séparés est compliqué par le fait que les procédures ne peuvent pas être des fonctions, ni utiliser `ByRef` arguments. Le moyen le plus simple pour retourner des valeurs consiste à utiliser le <xref:System.ComponentModel.BackgroundWorker>composant pour gérer vos threads et déclencher un événement à la fin de la tâche et traiter les résultats avec un gestionnaire d’événements.</xref:System.ComponentModel.BackgroundWorker>  
  
 L’exemple suivant retourne une valeur en déclenchant un événement à partir d’une procédure en cours d’exécution sur un thread séparé :  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 Vous pouvez fournir des paramètres et valeurs de retour aux threads de pool de threads à l’aide de l’option `ByVal` variable objet d’état de la <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>méthode.</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> Threads du composant timer thread prennent également en charge un objet d’état à cet effet. Pour plus d’informations sur le regroupement de threads et les composants Timer thread, consultez la page [le regroupement de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[le regroupement de threads](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) et [minuteries de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Multithreading avec le composant BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)   
 [(Visual Basic) de regroupement des threads](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)   
 [Synchronisation de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)   
 [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [Applications multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Multithreading dans les composants](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
