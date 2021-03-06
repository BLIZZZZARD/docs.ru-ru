---
title: "Примеры REF CURSOR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c9d282aba600d2475594887844ef19fc8eea374f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="ref-cursor-examples"></a>Примеры REF CURSOR
Примеры REF CURSOR состоят из трех следующих примеров Microsoft Visual Basic, в которых демонстрируется использование REF CURSOR.  
  
|Пример|Описание:|  
|------------|-----------------|  
|[Параметры REF CURSOR в объекте OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|В этом примере выполняется хранимая процедура PL/SQL, которая возвращает параметр REF CURSOR и считывает значение через <xref:System.Data.OracleClient.OracleDataReader>.|  
|[Извлечение данных из нескольких REF CURSOR с использованием OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|В этом примере выполняется PL/SQL, хранимая процедура, которая возвращает два параметра REF CURSOR и считывает значения с использованием **OracleDataReader**.|  
|[Заполнение DataSet с помощью одного или нескольких параметров REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|В этом примере выполняется хранимая процедура PL/SQL, которая возвращает два параметра REF CURSOR и заполняет набор <xref:System.Data.DataSet> возвращенными строками.|  
  
 Чтобы использовать эти примеры, может потребоваться создать таблицы Oracle; кроме того, необходимо создать пакет и текст пакета PL/SQL.  
  
## <a name="creating-the-oracle-tables"></a>Создание таблиц Oracle  
 В этих примерах используются таблицы, которые определены в схеме Oracle Scott/Tiger. Схема Oracle Scott/Tiger имеется в большинстве установок Oracle. Если этой схемы не существует, чтобы создать таблицы и индексы для этих примеров, можно использовать командный файл SQL в {OracleHome}\rdbms\admin\scott.sql.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Создание пакета и текста пакета Oracle  
 Для этих примеров требуется наличие на вашем сервере следующих пакетов и текста пакета PL/SQL. Создайте на сервере Oracle следующий пакет Oracle.  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 На сервере Oracle создайте следующий текст пакета Oracle.  
  
```  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS   
        V_CURSOR T_CURSOR;   
    BEGIN   
        IF N_EMPNO <> 0   
        THEN  
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO   
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE   
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;   
    END OPEN_ONE_CURSOR;   
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS   
        V_CURSOR1 T_CURSOR;   
        V_CURSOR2 T_CURSOR;   
    BEGIN   
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;   
        DEPTCURSOR := V_CURSOR2;   
    END OPEN_TWO_CURSORS;   
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a>См. также  
 [REF CURSOR в Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [Центр разработчиков наборов данных и управляемых поставщиков ADO.NET](http://go.microsoft.com/fwlink/?LinkId=217917)
