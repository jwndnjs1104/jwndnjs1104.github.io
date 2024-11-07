---
title: TripMaven
date: 2024-10-10 00:00:00 +09:00
categories: [프로젝트, 팀 프로젝트]
tags:
  [
    태그1,
    태그2,
    태그3
  ]

---

## <b><span style="color: steelblue; visibility: hidden;">TripMaven</span></b>
![TripMaven_Landing](assets/img/TripMaven_Landing.png)

<!-- 글 영역 -->
<div style="flex-grow: 1;">
  <table style=" background: none; width: 100%;">
    <tr style=" background: none;">
      <th style="width: 120px; white-space: nowrap; flex-shrink: 0; text-align:center">소개</th>
      <td>
        <span style="font-size: 90%">AI기술을 통한 여행가이드 서비스 교육 평가 및 개인 역량 진단 및 향상을 제공</span><br/>
      </td>
    </tr>
    <tr style=" background: none;">
      <th style="width: 120px; white-space: nowrap; flex-shrink: 0;text-align:center">기간/인원</th>
      <td>
        <span style="font-size: 90%">2024.08.17 ~ 2024.09.20</span><br/>
        <span style="font-size: 90%">7명</span>
      </td>
    </tr>
    <tr style=" background: none;">
      <th style="width: 120px; white-space: nowrap; flex-shrink: 0;text-align:center">핵심 기능</th>
      <td>
        <span style="font-size: 90%">음성 데이터 분석을 통한 가이드 피드백</span><br/>
        <span style="font-size: 90%">동영상 얼굴 분석을 통한 가이드 피드백</span><br/>
        <span style="font-size: 90%">가이드 자신만의 여행상품 기획</span><br/>
        <span style="font-size: 90%">가이드와 고객간 실시간 채팅</span>
      </td>
    </tr>
    <tr style=" background: none;">
      <th style="width: 120px; white-space: nowrap; flex-shrink: 0;text-align:center">팀 성과</th>
      <td>
        <span style="font-size: 90%">소셜 로그인</span><br/>
        <span style="font-size: 90%">이메일 인증</span><br/>
        <span style="font-size: 90%">영상,음성 인식 및 분석, 결과</span><br/>
        <span style="font-size: 90%">여행상품 게시 및 검색, 검색어 기반 유튜브 영상 추천</span><br/>
        <span style="font-size: 90%">날씨, 지역행사 API를 통한 지역별 정보 제공</span><br/>
        <span style="font-size: 90%">OCR을 활용한 가이드 인증 기능</span><br/>
        <span style="font-size: 90%">가이드, 고객 일대일 실시간 채팅 및 알림</span><br/>
        <span style="font-size: 90%">chatGPT기반 챗봇</span>
      </td>
    </tr>
    <tr style="border: none; background: none;">
      <th style="width: 120px; white-space: nowrap; flex-shrink: 0;text-align:center">개인 기여</th>
      <td>
        <span style="font-size: 90%; font-weight:bold">역할 요약: 백앤드/프론트앤드/DB 설계 및 생성, 코드 정리 및 최적화, 내부로직 구현, 리액트 각종 기능 구현  </span><br/><br/>
        <span style="font-size: 90%; font-weight:bold">세부 내용 </span><br/>
        > <span style="font-size: 90%">리액트, 스프링부트, FastAPI 서버 구축</span><br/>
        > <span style="font-size: 90%">공용 DB 구축 및 관리</span><br/>
        > <span style="font-size: 90%">DB설계, ERD 작성</span><br/>
        > <span style="font-size: 90%"></span><br/>
        > <span style="font-size: 90%">표정 및 음성 분석</span><br/>
        > <span style="font-size: 90%">실시간 채팅 및 알림 구현</span><br/>
        > <span style="font-size: 90%">자격증 OCR 및 셀레니움을 통한 인증</span>
      </td>
    </tr>
  </table>
</div>

- ### MindMap
![TripMaven_MindMap](assets/img/TripMaven_MindMap.png)

- ### ER Diagram
![TripMaven_ERD](assets/img/TripMaven_ERD.png)

- ### UseCase Diagram
![TripMaven_UseCase](assets/img/TripMaven_UseCase.png)

- ### 사용한 언어/프레임워크/라이브러리/Tool
![TripMaven_Tools](assets/img/TripMaven_Tools.png)

- ### 전반적인 아키텍처 구조
![TripMaven_EntireArchitecture](assets/img/TripMaven_EntireArchitecture.png)

- #### 채팅(MQTT) 아키텍처 구조
![TripMaven_MQTTArchitecture](assets/img/TripMaven_MQTTArchitecture.png)

- #### AI 서비스, 표정 분석 아키텍처 구조
![TripMaven_VideoAnalysisArchitecture](assets/img/TripMaven_VideoAnalysisArchitecture.png)

- #### AI 서비스, 음성 데이터 분석 아키텍처 구조
![TripMaven_VoiceAnalysisArchitecture](assets/img/TripMaven_VoiceAnalysisArchitecture.png)

- #### 가이드 자격증 확인 아키텍처 구조
![TripMaven_VerifyLicenseArchitecture](assets/img/TripMaven_VerifyLicenseArchitecture.png)