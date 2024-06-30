# *목표*

최근 생체 정보를 이용한 인증은 대세다. 플레이스토어부터 금융 결제까지 지문 등의 생체 정보로 인증하는 사례가 늘어나고 있다.     
이에 따라 지문 인증을 활용한 간단한 샘플을 작성하면서 사용법을 익히고 향후 프로젝트에 기능을 적용하고 활용하는데 의의가 있다.   

## fingerprint 오픈소스 라이브러리 의존성 추가
```kotlin
// 지문인식 라이브러리 추가
    implementation("me.aflak.libraries:fingerprintdialog:2.4.2")
```
## 레이아웃 
![image](https://github.com/chihyeonwon/QuizLock/assets/58906858/b8df9ee9-461a-4b90-a830-23992afb1c47)
```
간단한 버튼을 가운데 배치하였습니다.
```

## 기능 구현
![2024-06-30 16;23;58](https://github.com/chihyeonwon/QuizLock/assets/58906858/81c36126-e5c9-4410-9e59-78c47763d980)
```kotlin
button.setOnClickListener {

            // FingerPrintDialog로 지문인증을 쉽게 사용 가능
            // 사용법은 AlertDialog의 빌더 패턴과 유사
            FingerprintDialog.initialize(this)
                .title("지문인증")
                .message("지문으로 인증합니다.")
                .callback(object : FingerprintCallback {
                    // 인증 성공인 경우의 콜백 함수
                    override fun onAuthenticationSuccess() {
                        Toast.makeText(applicationContext, "인증", Toast.LENGTH_SHORT).show()
                    }

                    // 인증 실패인 경우의 콜백 함수
                    override fun onAuthenticationCancel() {
                        Toast.makeText(applicationContext, "인증 실패", Toast.LENGTH_SHORT).show()
                    }
                })
                .show()
        }
```
```
버튼을 눌렀을 때 FingerprintDialog의 제목과 메시지를 초기화하고 다이얼로그의 형태로 사용자에게 제공한다음
```

## 인증 성공 시
```kotlin
// 인증 성공인 경우의 콜백 함수
                    override fun onAuthenticationSuccess() {
                        Toast.makeText(applicationContext, "인증", Toast.LENGTH_SHORT).show()
                    }
```
```
인증 성공 시의 콜백 함수 안에 intent로 적절한 화면을 보여준다는 등의 로직을 구현할 수 있을 것이다.
향후 프로젝트에 로그인 기능을 구현하거나 인증 기능을 구현할 때 함께 사용해보면 좋을 것 같다는 생각이 들었다.
```

