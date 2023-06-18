 
#  More Than Us 

###### _하이미디어 아카데미  Final Project_            
[이준석](https://github.com/dlwnstjr0310), [김규철](), [김태훈](), [김유림](), [정현우](https://github.com/heyw00)
  
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


## Role & Works

<details>
<summary>이준석 ( 과정, 강의, 캘린더 )</summary>
<div markdown="1">

 <br>
<details> 
	<summary>과정</summary>
  <br>
  <br>
 <details>

<summary>실행영상</summary>
	 
![과정 실행영상](https://github.com/Insa-dong/.github/assets/126157268/7f6f6afd-fed5-47ff-aa7d-2d0ea2cdae10)
 </details>
 <br>
 <br>

> CRUD 와 검색기능 구현
- 과정 코드로 회차 조회시 한번의 통신으로 List 를 리턴받습니다.

	<summary>Service</summary>
	
	```java
	Pageable pageable = PageRequest.of(page - 1, 7, Sort.by("trainingCode").descending());

	Page<Training> foundList = trainingRepository.findByTrainingDeleteYn(pageable, "N");
	Page<TrainingDTO> foundDTOList = foundList.map(training -> modelMapper.map(training, TrainingDTO.class));
	List<Long> trainingCodeList = foundList.map(Training::getTrainingCode).toList();
	List<Long> foundCountList = studyRepository.findByTrainingCodes(trainingCodeList);

	List<TrainingDTO> list = foundDTOList.toList();

	for (int i = 0; i < foundCountList.size(); i++) {
		list.get(i).setStudyCount(foundCountList.get(i));
	}

	return new PageImpl<>(list, pageable, trainingRepository.countByTraining());
	```
	
	<summary>Repository</summary>
	
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
<br>

<details> 
	<summary>강의</summary>
  <br>
  <br>
 <details>

<summary>실행영상</summary>


![강의 실행영상](https://github.com/Insa-dong/.github/assets/126157268/ca1e4ff9-bfc7-44cf-887e-ba364153418e)

</details>

  <br>
  <br>
  
  > CRUD 와 검색기능 구현

</details>

<br>

<details>
<summary>캘린더</summary>
	<br>
	<br>
	
 <details>
<summary>실행영상</summary>

	
![캘린더 실행영상](https://github.com/Insa-dong/.github/assets/126157268/dca7b151-202e-4b29-a78c-78c72a059d2f)
</details>

<br>
<br>

> CRUD 와 정렬기준 변경 구현


</details>
</details>






<details>
<summary>정현우 ( 근태, 연차 )</summary>
<div markdown="1">

 <br>

### ⌚️ 근태
  <br>

 실행영상

 <br>

 > 출퇴근 기록과 그에 대한 조회
 - 출근 시간과 퇴근 시간을 등록합니다.
 	- 출근 시간 등록 전에는 퇴근 시간을 등록 할 수 없습니다.
 	- 출퇴근 시간은 재등록할 수 없습니다.
 - 근무 시간을 타이머로 보여줍니다.
 - 내 근태 기록(출근일, 출근시간, 퇴근시간, 연차여부)을 페이징 처리된 목록으로 조회할 수 있습니다.
   
 <br>
 
 > 출퇴근 시간 수정과 조회
 - 관리자의 경우 모든 구성원의 근태 정보를 페이징 처리된 목록으로 조회할 수 있습니다.
 - 구성원의 근태 정보를 날짜(출근일)별로 검색하여 조회할 수 있습니다.
 - 관리자의 경우 구성원의 출퇴근 시간을 수정할 수 있습니다.

<br>
<br>

### 🚥 연차
  <br>

 실행영상
 
 <br>

 > 내 연차 조회 
 - 내 연차 현황(총 연차, 사용 연차, 남은 연차)을 보여줍니다.
	- 총 연차는 현재 15개로 고정하였습니다.
	- 사용 연차는 승인된 연차 일수 만큼 늘어나며, 취소 될 경우 복구됩니다.
 	- 남은 연차는 총 연차에서 사용 연차를 제외한 값입니다. 
 - 예정 연차 : 신청한 연차의 정보와 승인 상태를 보여줍니다.
 - 사용 기록 : 지난 연차 사용 기록을 보여주며, 연도별로 조회할 수 있습니다.
<br>
 
 > 연차 신청과 취소
 - 연차 신청하기를 통해 연차 정보를 기입, 제출하여 자신의 팀장에게 연차 신청을 할 수 있습니다.
 - 알러트 창을 통해 제약 사항을 알려줍니다.
 	- 필수 입력 사항 (연차 종류, 시작일, 종료일, 신청 사유)를 반드시 등록하도록 합니다.
 	- 이미 신청한 날짜가 포함될 경우 신청할 수 없습니다. 
 	- 신청하려는 기간이 남은 연차보다 많을 경우 신청할 수 없습니다.
- 신청취소 버튼을 통해 연차 신청을 취소하여 데이터를 삭제합니다.

   <br>
   
 > 구성원 연차 조회 및 결재
 - 관리자는 모든 구성원의 연차 현황(총 연차, 사용 연차, 남은 연차)를 조회, 검색할 수 있습니다.
 - 팀장은 자신의 팀원의 연차 현황을 조회, 검색할 수 있습니다.
 - 팀장은 자신에게 올라온 연차 신청을 조회할 수 있으며, 반려 또는 승인 처리할 수 있습니다.
 	- 모든 검색은 이름, 부서, 잔여 연차 별로 조회할 수 있습니다. (잔여 연차는 검색어 이상의 정보 조회)

   <br>
</details>
<details>
<summary>김유림 ( 구성원, 휴직 )</summary>
<div markdown="1">





 
</details>
<details>
<summary>김규철 ( 로그인, 내정보, 공지사항 )</summary>
<div markdown="1">





 </details>
<details>
<summary>김태훈 ( 수강생, 강사 )</summary>
<div markdown="1">






</details>
   
