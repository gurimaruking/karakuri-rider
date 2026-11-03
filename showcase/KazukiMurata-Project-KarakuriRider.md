# Karakuri Rider

- **Participant:** Kazuki Murata
- **Stage completed:** 1
- **Repository:** https://github.com/gurimaruking/karakuri-rider
- **Demo video:** TODO
- **Community post:** TODO (Discord thread permalink)
- **License:** MIT

## Summary

Karakuri Rider is an original mechanical doll riding a toy tricycle that drives itself. Japanese karakuri dolls were the robots of the Edo period: clockwork figures that served tea or wrote characters. This project brings that idea to a modern maker space in Akihabara, Tokyo. The toy tricycle's receiver is replaced by a D-Robotics RDK X5, which reads a wide-angle camera hidden in the headlight and steers and drives the tricycle with a model trained from manual driving data, in the style of DonkeyCar. The doll on top is part of the show: its face is 3D-printed, its jaw opens and closes, and its eyes light up when it sees people. The target is to complete a track on its own, as fast as the little tricycle can go, with all inference on the board's BPU.

Stage 1 result: TODO (board bring-up, camera, YOLO on the BPU with measured FPS).

## Technical Highlights

- **RDK board / image:** RDK X5 8 GB, RDK OS 3.5.0 (Desktop)
- **AI model and runtime:** TODO (Stage 1: YOLO sample on the BPU; Stage 3: driving model on the BPU)
- **Sensors and actuators:** wide-angle camera; steering servo and rear drive motor via PCA9685 + TB6612; doll jaw servo and eye LEDs
- **ROS 2 design:** planned camera → driving model → steering/throttle, plus person detection → doll expression
- **BPU evidence and performance:** TODO

## Architecture

To be added in Stage 2 (Mermaid diagram).

## Links and Evidence

- Flash and SSH evidence: TODO
- Sensor proof: TODO
- AI output: TODO
- Benchmarks: TODO

## Known Limitations and Safety

The tricycle is a moving robot. A wireless emergency stop cuts drive power, speed is capped in software, and test runs are done on a closed course. Details will be documented in Stage 3.

---

I agree that this showcase document may be used by the Robotics Dream Keeper Challenge organizers for program promotion, judging, and archives as described in the official README.
