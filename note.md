비동기
: 작업 대기 시간 발생하면 다른 작업 처리
- import asyncio

코루틴(coroutine)
- 비동기 관련 함수, 실행 멈췄다가 다시 할 수 있음
- 여러 번 호출되거나 특정 지점에서 중단 가능
- `async def` 로 정의 -> 코루틴 객체 반환 -> `asyncio.run()`으로 실행

await
- 비동기 함수 실행 중지
- 코루틴 내에서 await 로 프로그램 제어권 넘김
- 비동기 함수 내에서만 사용 가능
- await 지원하는 객체에서만 사용 가능

Event Loop
- 비동기 작업 관리
- 반복적으로 비동기 작업의 완료 같은 이벤트를 감지하고 관리
- Task Queue(: 진행 예정 작업)에 있는 작업들 관리
- 루프 내에서는 비동기 함수 사용 , 동기 함수 사용 시 이점 사라짐
- `asyncio.run()` 내부적으로 Event Loop 실행

Fast API
- 비동기 프로그래밍 쉽게 지원
- 동기 비동기 함수 둘 다 구현 가능
    BUT, 동기 함수는 그냥 실행해도 실행 함수 내부에서 starlette의 `run_in_threadpool` 함수로 별도의 쓰레드 풀에서 실행됨 > 비동기 함수처럼 작용
- uvicorn, starlette 사용
    - uvicorn: ASGI 구현한 간단한 서버 (ASGI: 비동기 파이썬 웹 앱플리케이션 표준 인터페이스)
    - starlette: uvicorn 위에서 동작, 웹 서버에 다양한 기능 제공