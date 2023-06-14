 
#  More Than Us 

###### _하이미디어 아카데미  Final Project_            
[이준석](https://github.com/dlwnstjr0310), [김규철](), [김태훈](), [김유림](), [정현우]()
  
  > 개발: 2023.05.09. ~ 2023.06.09.

## Purpose 
- 학원 내 인사, 업무 관리 업무를 효율적으로 처리하고 관리하기 위한 프로그램을 개발하는 프로젝트입니다. 
- 이 프로그램은 행정부서와 조직 내 모든 직원들이 사용할 수 있으며, 다양한 기능들을 제공하여 인사 업무의 효율성을 극대화할 수 있습니다.

## Tech
> Front

<img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=white"/>&nbsp;
<img src="https://img.shields.io/badge/React Router-CA4245?style=flat-square&logo=reactrouter&logoColor=white"/>&nbsp;
<img src="https://img.shields.io/badge/Redux-764ABC?style=flat-square&logo=redux&logoColor=white"/>&nbsp;
<img src="https://img.shields.io/badge/HTML-E34F26?style=flat-square&logo=html5&logoColor=white"/>&nbsp;
<img src="https://img.shields.io/badge/CSS-1572B6?style=flat-square&logo=css3&logoColor=white"/>&nbsp;
<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=white"/>&nbsp;
<img src="https://img.shields.io/badge/Axios-5A29E4?style=flat-square&logo=axios&logoColor=white"/>&nbsp;

> Back

<img src="https://img.shields.io/badge/Java-5382a1?style=flat-square&logo=java&logoColor=white"/>&nbsp;
<img src="https://img.shields.io/badge/Spring-6DB33F?style=flat-square&logo=spring&logoColor=white"/>&nbsp;
<img src="https://img.shields.io/badge/Spring Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white"/>&nbsp;
<img src="https://img.shields.io/badge/Spring Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white"/>&nbsp;
<img src="https://img.shields.io/badge/Oracle-F80000?style=flat-square&logo=oracle&logoColor=white"/>&nbsp;


## Role 
##### 이름을 클릭해 보세요!


<details>
<summary>이준석</summary>
<div markdown="1">
	
# 과정

 <details>
<summary>과정 실행영상</summary>
	 
![과정 실행영상](https://github.com/Insa-dong/.github/assets/126157268/7f6f6afd-fed5-47ff-aa7d-2d0ea2cdae10)
 </details>

> CRUD 와 검색기능 구현
- 과정 코드로 회차 조회시 한번의 통신으로 List 를 리턴받습니다.
  <details>
	  <summary>Service</summary>
```java
@Query(value = "SELECT 
		nvl(max(s.studyCount), 0) 
	  FROM Study s 
	 RIGHT JOIN s.training t 
	 WHERE t.trainingCode IN :trainingCodeList 
	 GROUP by t.trainingCode 
	 ORDER by t.trainingCode DESC")
List<Long> findByTrainingCodes(List<Long> trainingCodeList);
```
  </details>
  ```java
  @Query(value = "SELECT 
  			nvl(max(s.studyCount), 0) 
  		  FROM Study s 
  	    	 RIGHT JOIN s.training t 
  		 WHERE t.trainingCode IN :trainingCodeList 
  		 GROUP by t.trainingCode 
  		 ORDER by t.trainingCode DESC")
  List<Long> findByTrainingCodes(List<Long> trainingCodeList);
  ```

	
<br>

# 강의

 <details>
<summary>과정 실행영상</summary>

![강의 실행영상](https://github.com/Insa-dong/.github/assets/126157268/ca1e4ff9-bfc7-44cf-887e-ba364153418e)
</details>

> CRUD 와 검색기능 구현
 

# 캘린더

 <details>
<summary>캘린더 실행영상</summary>

![캘린더 실행영상](https://github.com/Insa-dong/.github/assets/126157268/dca7b151-202e-4b29-a78c-78c72a059d2f)
</details>

> CRUD 와 정렬기준 변경 구현
</details>


