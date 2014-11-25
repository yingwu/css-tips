## 选择器(selectors) ##
> 官方TR(http://www.w3.org/TR/selectors/)

- **类型选择器(`<E>`)**

	`h1 { color: green }`

- **通用选择器 (`*`)**

	` *{margin:0;}`

- **ID选择器(`<E id="xx">`)**

	`#test{color:red;}`

- **类选择器(`<E class="x1 x2"> .x1 or .x2`)**
	
	` .x1{color:red;}`

- **属性选择器(`<E name="xx">  E[name="xx"]`)**
			
	`E[name=xx]{color:red;}`

	* [att] 有这个属性att
	* [att=val] 有属性att,等于val
	* [att~=val] 有属性att, att的值是以空格分割的字符串列表,其中一个子串等于val
	* [att|=val] 有属性att,以val开头
	* [att^=val]有属性att,不等于val
	* [att$=val] 有属性att,以val结束
	* [att*=val] 有属性att,val是其值的子字符串

- **伪类[Pseudo-classes]选择器**
			
		a:link{color:red}
		a:visited{color:blue;}

	* :link
	* :visited
	* :hover
	* :active
	* :focus
	* :target
	* :lang
	* :enabled
	* :disabled  
	* :checked  radio|checkbox
	* :nth-child()
	
		`tr:nth-child(odd) = tr:nth-child(2n+1) 奇数行`
		`tr:nth-child(even) = tr:nth-child(2n+0) 偶数行`
		`tr:nth-child(1){color:red} 第一行`

	* :nth-last-child()
	* :nth-of-type()
	
		`img:nth-of-type(2n+1) { float: right; }`

	* :nth-last-of-type
	* :first-child
	
		`div>p:first-child{color:red;}`

	* :last-child
	* :first-of-type
	* :last-of-type
	* :only-child
	* :only-of-type
	* :empty
- **否定符选择器 (:not)**
		
	`button:not([DISABLED])`

	`button:not(.edit)`

- **伪元素(Pseudo-elements)**
	* ::first-line  首行
	
		`p::first-line{text-transform: uppercase}`

	* ::first-letter 首字母
	* ::before
	* ::after
		
		`p.icon::after{content:"A"}`

- **后代选择器(Descendant combinator)**
	
	`div p{color:red;}`

- **子元素选择器(Child combinator)**
	
	`div > p{color:red;}`


- **兄弟选择器(Sibling combinators)**
	
	`div + p`

- **一般兄弟选择器(General sibling combinator)**
	
	`div ~ p`

- **选择器组(Groups of selectors)**  
	
	`h1, h2, h3 { font-family: sans-serif }`

* **选择器的优先级(priority)|特异度(specificity)**
 
	> 当一个元素同时满足多个选择器规则时,样式若重复定义,优先采用哪个选择器定义的样式
	
	* 算法(计算a-b-c三个值,结果即优先级)
		
		1. count the number of ID selectors in the selector (= a)
		1. count the number of class selectors, attributes selectors, and pseudo-classes in the selector (= b)
		1. count the number of type selectors and pseudo-elements in the selector (= c)
		1. ignore the universal selector

	* 举例
	
				*				/* a=0 b=0 c=0 -> specificity =   0 */
				LI              /* a=0 b=0 c=1 -> specificity =   1 */
				UL LI           /* a=0 b=0 c=2 -> specificity =   2 */
				UL OL+LI        /* a=0 b=0 c=3 -> specificity =   3 */
				H1 + *[REL=up]  /* a=0 b=1 c=1 -> specificity =  11 */
				UL OL LI.red    /* a=0 b=1 c=3 -> specificity =  13 */
				LI.red.level    /* a=0 b=2 c=1 -> specificity =  21 */
				#x34y           /* a=1 b=0 c=0 -> specificity = 100 */
				#s12:not(FOO)   /* a=1 b=0 c=1 -> specificity = 101 */