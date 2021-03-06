# Втора лабораториска вежба по Софтверско инженерство

## Нина Костоска, бр. на индекс 171151

### Control Flow Graph
![Capture](https://user-images.githubusercontent.com/73118689/120199253-5293e480-c223-11eb-8463-55363a81bf06.PNG)
### Цикломатска комплексност
Цикломатската комплексност на овој граф е 8 и може да се најде на два начини. 
Првиот начин е со формулата e-v+2, каде се наоѓа бројот на јазли и рабови, во овој случај имав 25 рабови, а 19 јазли,
според Control Flow Graph што го нацртав. 25-19+2=8 региони. 
Вториот начин е со помош на предикати, со формулата P+1, каде се бројат разгранувањата на if-овите и for-от.
Во тој случај имаме 7+1=8.
### Тест случаи според критериумот Multiple condition
Кога се работи за multiple condition критерумиот. Пример кога се работи за || и &&, минималниот број на тестови е 3.
Ова може да се покаже со табелата на вистинитост.
##### p|q |p&&q |p||q|   AND-- TT, TF, FX
##### T|T |  T  |  T |   OR-- TX, FT, FF
##### T|F |  F  |  T |
##### F|T |  F  |  T |
##### F|F |  F  |  F |
За AND може да забележиме дека кога еден од условите е грешен целиот израз е грешен.
Што значи дека за последните два реда ќе запишеме FX, што значи доволни ќе ни се 3 тест примери
еден за ТТ, еден за ТF и еден за FX.
Истото е и за OR, само што во овој случај, кога еден услов е точен целиот израз е точен.
Што значи дека за првите два реда од табелата ќе запишеме ТX, и затоа ќе ни се потребни 3 тест примери,
еден за TX, еден за FT, еден за FF.
Пример ако внесеме 3 часа 30 минути и 20 секунди, за уловот if (hr < 0 || hr > 24), условот ќе падне бидејќи имаме 3h, и двата услови се грешни,
но доколку бројот на часови го смениме да биде пример -1, првиот услов ќе е точен и ке влеземе во разгранувањето,
каде имаме нов услов if (hr < 0),овде условот ќе испадне точен. Доколку внесевме 3 часа 30 минути и 78 секунди, условот else if (hr < 24) ќе помине за точен.
Но, условот if (min < 0 || min > 59) ќе падне бидејќи двата услови се грешни, барем еден да беше точен ќе поминеше.
Но, условот if (sec >= 0 && sec <= 59), првот услов ќе помине ќе биде точно, но на вториот услов ќе падне и точаш целиот if услов ќе биде грешен.
### Тест случаи според критериумот Every brantch
За Every brantch, branch-ovite ги пишуваме како јазол-јазол.
За тука направив неколку теста, наведени се подоле.
#####       |3h20m30s |3h20m78s |0h78m10s |24h0m0s |-1h20m0s |25h66m85s
### 1-2	    |    *	  |    *	  |    *    |   *	   |   *     |   *
### 2-3.1	  |    *    |    *    |    *    |   *    |   *	   |   *
### 3.2-456	|    *	  |    *	  |    *	  |   *	   |   *     |   *
### 3.2-456	|    *	  |    *	  |    *	  |   *	   |   *     |   *
### 3.2-24	|    *	  |    *	  |    *	  |   *	   |   *	   |   *
### 4,5,6-7	|    *    | 	 *    |    *    |   *    |   *	   |   *
### 7-8			|		      |         |         |        |   *	   |   *
### 7-12	  |    *	  |    *	  |    *	  |   *	   |   *	   |
### 8-9			|		      |         |         |        |   *	   |
### 8-11		|				  |         |         |        |         |   *
### 9-3.3		|			    |         |         |        |   *     |
### 11-3.3	|					|         |         |        |         |   *
### 12-20	  |    *	  |    *	  |    *	  |   * 	 |   *	   |
### 12-13	  |    *	  |    *	  |    *		|        |   *	   |
### 20-21	  |		      |         |         |   *		 |         |
### 20-23		|				  |         |         |        |         |   *
### 21-3.3	|			    |         |         |   *		 |         |
### 23-3.3	|					|         |         |        |         |   *
### 13-14		|	        |         |    *		|        |         |
### 13-16	  |    *	  |    *		|	        |        |   *	   |
### 14-3.3	|		      |         |    *		|        |         |
### 16-19		|         |    *		|	        |        |         |
### 19-3.3	|	        |    *		|         |	       |         |
### 16-17	  |   *			|	        |         |        |   	     |
### 17-3.3	|   *			|	        |         |        |   *     |
### 3.3-3.2	|   *	    |    *    |    *    |   *	   |   *	   |   *
Од примерот може да забележиме дека се опфатени сите branches, што значи дека може да закличиме
дека минимум тест примери за овој пример/граф се 6.
Направив еден услов каде и часот, минутите и секундите се точни, еден каде сите се грешни, еден каде часот е негативен број,
односно помал од 0, еден каде само минутите се грешни, еден каде само секундите се грешни и еден каде го опфаќам условот дека часот е 24, мин 0 и сек 0.
Преку овие тест примери се опфатени сите можни сценарија.
