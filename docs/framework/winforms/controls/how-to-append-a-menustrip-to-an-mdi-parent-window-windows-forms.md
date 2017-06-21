---
title: "Практическое руководство. Добавление элемента управления в родительское окно MDI-приложения (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "MDI - интерфейс, объединение пунктов меню"
  - "MenuStrip - элемент управления [Windows Forms], присоединение"
  - "MenuStrip - элемент управления [Windows Forms], слияние"
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Практическое руководство. Добавление элемента управления в родительское окно MDI-приложения (Windows Forms)
В некоторых приложениях вид дочернего окна многодокументного интерфейса \(MDI\) может отличаться от родительского окна MDI.  Например, родительским окном MDI может быть электронная таблица, а дочерним окном MDI — диаграмма.  В этом случае может потребоваться дополнить содержимое меню родительского окна MDI содержимым меню дочерней MDI\-формы, по мере того как активируются дочерние окна MDI различных типов.  
  
 В следующей процедуре используются свойства <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction> и <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> для добавления меню дочернего окна MDI в меню родительского окна MDI.  При закрытии дочернего окна MDI удаляются пункты меню, добавленные из родительского окна MDI.  
  
 См. также [Приложения с интерфейсом MDI](http://msdn.microsoft.com/library/xyhh2e7e\(v=vs.110\)).  
  
### Добавление пункта меню в родительское окно MDI  
  
1.  Создайте форму и присвойте ее свойству <xref:System.Windows.Forms.Form.IsMdiContainer%2A> значение `true`.  
  
2.  Добавьте <xref:System.Windows.Forms.MenuStrip> на `Form1` и присвойте свойству <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> для элемента <xref:System.Windows.Forms.MenuStrip> значение `true`.  
  
3.  Присвойте свойству <xref:System.Windows.Forms.ToolStripItem.Visible%2A> элемента `Form1`<xref:System.Windows.Forms.MenuStrip> значение `false`.  
  
4.  Добавьте пункт меню верхнего уровня в `Form1`<xref:System.Windows.Forms.MenuStrip> и присвойте его свойству <xref:System.Windows.Forms.Control.Text%2A> значение `&File`.  
  
5.  Добавьте пункт подменю в элемент меню `&File` и присвойте его свойству <xref:System.Windows.Forms.Form.Text%2A> значение `&Open`.  
  
6.  Добавьте в проект форму, добавьте <xref:System.Windows.Forms.MenuStrip> на форму и присвойте его свойству <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> элемента `Form2`<xref:System.Windows.Forms.MenuStrip> значение `true`.  
  
7.  Добавьте пункт меню верхнего уровня в `Form2`<xref:System.Windows.Forms.MenuStrip> и присвойте его свойству <xref:System.Windows.Forms.Form.Text%2A> значение `&Special`.  
  
8.  Добавьте два подменю к пункту меню `&Special` и присвойте их свойствам <xref:System.Windows.Forms.Form.Text%2A> значения `Command&1` и `Command&2` соответственно.  
  
9. Присвойте свойству <xref:System.Windows.Forms.MergeAction> элементов меню `&Special`, `Command&1` и `Command&2` значение <xref:System.Windows.Forms.MergeAction>.  
  
10. Создайте обработчик событий для события <xref:System.Windows.Forms.Control.Click> элемента `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. В обработчик событий вставьте код, аналогичный приведенному в следующем примере для создания и отображения новых экземпляров `Form2` в качестве дочерних окон MDI `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
  
    ```  
  
     \[C\#\]  
  
    ```  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
  
    ```  
  
12. Поместите код, аналогичный приведенному в следующем примере, в `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>, для регистрации обработчика событий.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
  
    ```  
  
## Компиляция кода  
 Для этого примера требуются:  
  
-   два элемента управления <xref:System.Windows.Forms.Form> с именами `Form1` и `Form2`;  
  
-   элемент управления <xref:System.Windows.Forms.MenuStrip> на `Form1` с именем `menuStrip1` и элемент управления <xref:System.Windows.Forms.MenuStrip> на `Form2` с именем `menuStrip2`;  
  
-   ссылки на сборки <xref:System?displayProperty=fullName> и <xref:System.Windows.Forms?displayProperty=fullName>.