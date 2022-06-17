# map
## 맵 뷰로 지도를 나타내며 핀치 제스처를 사용해 사진 확대 및 축소하는 앱 만들기

내가 직접 만들어 본 앱으로는 맵 뷰와 핀치 제스처를 사용하여 지도를 만들어 보았다.
우리는 일상생활에서 많은 사람들이 길을 찾을때 지도앱을 사용한다. 그런 점을 생각해보며 길을 찾을땐 더더욱 위치를 정확히 알기 위해서는 확대를 하는 일도 잦으니까 그것을 생각해보며 이 앱을 만들어보았다.

이 앱을 만들때는 일반적으로 맵 뷰를 만들때와 같은 방식으로 스토리보드가 꾸며지게 되는데 이 부분에서 핀치 제스처를 응용하여 넣었다.
- 코드로 설명 해보자면
₩₩₩
import UIKit
import MapKit
₩₩₩
이 맵킷은 지도를 확대, 축소 및 이동하는 등 지도에 관한 여러 기능을 제공한다. 따라서 사용자가 터치를 인식하여 기능을 수행하려면 이 작업이 필요하기 때문에 꼭 맵을 만들땐 넣어줘야한다.

그리고나서 응용을 했던 부분은
₩₩₩
    @IBOutlet var txtPinch: UILabel!
    @IBOutlet var mapView: MKMapView!
    @IBOutlet var lblLocationInfo1: UILabel!
    @IBOutlet var lblLocationInfo2: UILabel!
₩₩₩
이 부분인데 맵 뷰를 연결할때 핀치도 같이 연결하였다.

**지도에서 중요한 부분이라고 할 수 있는 부분은 이 부분이라고 생각이 드는데**
> 지도에는 정확도와 위치를 보기때문에 사용자에게 승인을 요구해야하며 위치 업데이트도 해야하기 때문에 이 코드가 필수로 들어가야한다고 생각이 든다.
₩₩₩
lblLocationInfo1.text = ""
        lblLocationInfo2.text = ""
        locationManager.delegate = self
        // 정확도를 최고로 설정
        locationManager.desiredAccuracy = kCLLocationAccuracyBest
        // 위치 데이터를 추적하기 위해 사용자에게 승인 요구
        locationManager.requestWhenInUseAuthorization()
        // 위치 업데이트를 시작
        locationManager.startUpdatingLocation()
        // 위치 보기 설정
        mapView.showsUserLocation = true
        mapView.delegate = self
₩₩₩
> 중요한 부분인 만큼 코드를 쓸때 주석을 사용하여 한번 더 어느 부분이 어느 역할을 하고있는지 알아볼 수 있도록 표시하였다.

이제 나머지 부분들은 맵 뷰 아래 레이블을 두개를 만들어서 하나는 현재위치가 나타나게, 또 하나는 설정해둔 장소의 이름이 뜨도록 표현하였다.

- 지도앱은 알아보기 조금 복잡한데 코드부분이 그러기 때문에 주석을 더 많이 사용하여 코드 내에서도 표현을 하려고 하였던거 같다. 이 앱은 누구나 있을거라고 생각하겠지만 원래 사람들애게 필요한 부분은 많이 언급되어 더욱더 발전한다고 생각하기 때문에 더 코드를 연습하여 점점 완벽한 앱을 만들 수 있도록 노력해야겠다.
