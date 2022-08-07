### [Frontend Web Performance: The Essentials](https://medium.com/@matthew.costello/frontend-web-performance-the-essentials-0-61fea500b180)

️Less Is More — The Browser Rendering Cycle, Hardware Acceleration, Compositor Layers, Tools & Examples

Device displays run at a certain number of frames per second.    
기기의 디스플레이들은 초당 특정 수의 프레임으로 실행됩니다.   

Browsers try to match this rate for a smooth user experience.   
브라우저는 원활한 사용자 경험을 위해 이 비율을 일치시키려고 합니다.

To output a new frame to the display, the browser must first complete its ‘rendering cycle’ or ‘pixel pipeline’.   
디스플레이에 새 프레임을 출력하려면 브라우저가 먼저 '렌더링 주기' 또는 '픽셀 파이프라인'을 완료해야 합니다.

The majority of devices run at 60 FPS.    
장비의 대부분은 60FPS로 실행됩니다.   

This allows for around a 16ms window to complete the rendering cycle, per frame.   
이를 통해 프레임당 렌더링 주기를 완료하는 데 약 16ms 시간이 소요됩니다.

Increased FPS means even smaller frame budgets; 120 FPS requires no more than 8ms spent per frame.
FPS가 증가하면 프레임 예산이 훨씬 더 작아집니다. 120FPS는 프레임당 8ms 이상을 소비하지 않습니다.

To make matters worse, browsers generally add some extra overhead and can take up to 4ms away from the frame budget;   
설상가상으로, 브라우저는 일반적으로 약간의 오버헤드를 추가하고 프레임 예산에서 최대 4ms가 추가될 수 있습니다.
more realistically we end up with around a 12ms budget to reach 60 FPS.      
현실적으로 60FPS에 도달하기 위한 예산으로 12ms가 걸립니다.
At 120 FPS that’s just 4ms per frame!
프레임당 4ms인 120 FPS에서!

If the browser is unable to meet the frame budget, frames get ‘dropped’, 
meaning it is outputting frames at a lower rate than the screen’s refresh rate.   
브라우저가 프레임 예산을 충족할 수 없는 경우 프레임이 드랍되어 화면의 재생빈도보다 낮은 속도로 프레임을 출력합니다.   

This leads to unsmooth motion, jitter, judder, or ‘jank’: 
a bad user experience, particularly if it is happening consistently.   
이는 특히 지속적으로 발생하는 경우 부드러운 동작, 지터, 떨림이나 잡음으로 이어집니다. 이는 특히 지속적으로 발생하는 경우 나쁜 사용자 경험입니다.