    _dispatcher = [WebSocketRailsDispatcher.alloc initWithUrl:[NSURL URLWithString:@"ws://localhost:3001/websocket"]];
    
    WebSocketRailsChannel *testChannel = [_dispatcher subscribe:[NSString stringWithFormat:@"user_%@", @([[VRTProfile currentUser] profileId])]];
    
    [testChannel bind:@"new_notification" callback:^(id data) {
        NSLog(@"new_notification : %@", data);
    }];
    
    [testChannel bind:@"update_notification" callback:^(id data) {
        NSLog(@"update_notification : %@", data);
    }];
