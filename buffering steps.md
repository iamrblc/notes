- [x] **1 Refactor final saving only**  
    Keep behavior unchanged. Make final ECG/ACC/recording CSV creation cleaner.
    
- [x] **2 Create session files at Start**  
    Create paths and headers immediately when recording starts.
    
- [x] **3 Append ECG/ACC during recording**  
    Use small buffers and flush to `_ecg.csv` / `_acc.csv` periodically.
    
- [x] **4 Generate `_recording.csv` on Stop**  
    Load saved ECG/ACC CSVs, reconstruct timestamps, merge ACC to ECG, detect R-peaks, save final quick-check file.
    
- [ ] **5 Add explicit app states**  
    Separate: disconnected, ready, recording, reconnecting, stopping.
    
- [ ] **6 Add safe recovery/abort path**  
    Ensure user can stop reconnect attempts, disconnect, destroy current BLE client, and return to a clean state.
    
- [ ] **7 Detect unexpected stream/connection loss**  
    Do not reconnect yet. Just flush buffers and show clear status.
    
- [ ] **8 Add interruptible reconnect loop**  
    Retry reconnecting at short intervals, but allow cancellation.
    
- [ ] **9 Use fresh BLE client on reconnect**  
    Do not reuse possibly stale Windows BLE client objects.
    
- [ ] **10 Auto-restart stream after reconnect**  
    Continue same session, same files, same experiment time-zero.
    
- [ ] **+1 Windows checkpoint**  
    Test stale-state behavior before refining reconnect further.
    