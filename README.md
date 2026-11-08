# lobin

This repository contains the initial architectural prototype code, which was developed in Rust before the project transitioned to C++.

This repository has been archived.

The license is AGPL v3.

## Test Code

```rust
use macroquad::prelude::*;
use lobin::vector::vector::Vector3;

#[macroquad::main("Physics Test")]
async fn main() {
    let mut pos = Vector3::new(400.0, 300.0, 0.0);
    let mut vel = Vector3::zero();
    let gravity = Vector3::new(0.0, -9.81, 0.0);
    let dt = 0.016;

    loop {
        vel = vel + gravity * dt;
        pos = pos + vel * dt * 100.0;

        if pos.y < 0.0 {
            pos.y = 0.0;
            vel.y *= -0.7;
        }

        clear_background(BLACK);
        draw_rectangle(pos.x, 600.0 - pos.y, 50.0, 50.0, RED); // y축 반전
        next_frame().await;
    }
}
```
