## Modbus Tcp for Android

### Introduce
This is a Modbus TCP example for Android.If You need the examples for RTU/ASCII ,You can call me.

### How to use
#### 1.Creat ModbusMaster

    ModbusFactory factory = new ModbusFactory();
    IpParameters params = new IpParameters();
	//Setting Ip Address and port
    params.setHost("192.168.0.101");
    params.setPort(502);
    params.setEncapsulated(false);
	//Creat ModbusMaster and set timeout and retry count
    ModbusMaster master = factory.createTcpMaster(params, true);
    // master.setRetries(4);
    master.setTimeout(2000);
    master.setRetries(0);

#### 2.Init ModbusMaster

    master.init();

#### 3.Read Coil(Child Thread)

	ModbusReq.readCoil(mModbusMaster, new OnRequestBack<boolean[]>() {
                        @Override
                        public void onSuccess(boolean[] booleen) {
                            Log.d(TAG, "readCoil onSuccess " + Arrays.toString(booleen));
                        }
    
                        @Override
                        public void onFailed(String msg) {
                            Log.e(TAG, "readCoil onFailed " + msg);
                        }
                    }, 1, 1, 2);

<img src="https://github.com/zgkxzx/Modbus4Android/blob/master/screenshot/read_coil.png" width = "1353" height = "500" alt="Read Coil" align=center />

#### 4.Read DiscreteInput(Child Thread)
	
	ModbusReq.readDiscreteInput(mModbusMaster, new OnRequestBack<boolean[]>() {
                        @Override
                        public void onSuccess(boolean[] booleen) {
                            Log.d(TAG, "readDiscreteInput onSuccess " + Arrays.toString(booleen));
                        }
    
                        @Override
                        public void onFailed(String msg) {
                            Log.e(TAG, "readDiscreteInput onFailed " + msg);
                        }
                    },1,1,5);

<img src="https://github.com/zgkxzx/Modbus4Android/blob/master/screenshot/read_discrete_input.png" width = "1353" height = "500" alt="Read DiscreteInput" align=center />

#### 5.Read HoldingRegisters(Child Thread)
	
	ModbusReq.readHoldingRegisters(mModbusMaster, new OnRequestBack<short[]>() {
                        @Override
                        public void onSuccess(short[] data) {
                            Log.d(TAG, "readHoldingRegisters onSuccess " + Arrays.toString(data));
                        }
    
                        @Override
                        public void onFailed(String msg) {
                            Log.e(TAG, "readHoldingRegisters onFailed " + msg);
                        }
                    }, 1, 2, 8);

<img src="https://github.com/zgkxzx/Modbus4Android/blob/master/screenshot/read_holding_register.png" width = "1353" height = "500" alt="Read HoldingRegisters" align=center />

#### 6.Read InputRegisters(Child Thread)
	
	 ModbusReq.readInputRegisters(mModbusMaster, new OnRequestBack<short[]>() {
                        @Override
                        public void onSuccess(short[] data) {
                            Log.d(TAG, "readInputRegisters onSuccess " + Arrays.toString(data));
                        }
    
                        @Override
                        public void onFailed(String msg) {
                            Log.e(TAG, "readInputRegisters onFailed " + msg);
                        }
                    }, 1, 2, 8);

<img src="https://github.com/zgkxzx/Modbus4Android/blob/master/screenshot/read_input_registers.png" width = "1353" height = "500" alt="Read InputRegisters" align=center />

#### 7.Write Coil(Child Thread)
	
	ModbusReq.writeCoil(mModbusMaster, new OnRequestBack<String>() {
                        @Override
                        public void onSuccess(String s) {
                            Log.e(TAG, "writeCoil onSuccess " + s);
                        }
    
                        @Override
                        public void onFailed(String msg) {
                            Log.e(TAG, "writeCoil onFailed " + msg);
                        }
                    },1,1,true);

<img src="https://github.com/zgkxzx/Modbus4Android/blob/master/screenshot/write_coil.png" width = "1353" height = "500" alt="Write Coil" align=center />

#### 8.Write Register(Child Thread)
	
	ModbusReq.writeRegister(mModbusMaster, new OnRequestBack<String>() {
                        @Override
                        public void onSuccess(String s) {
                            Log.e(TAG, "writeRegister onSuccess " + s);
                        }
    
                        @Override
                        public void onFailed(String msg) {
                            Log.e(TAG, "writeRegister onFailed " + msg);
                        }
                    },1,1,234);

<img src="https://github.com/zgkxzx/Modbus4Android/blob/master/screenshot/write_register.png" width = "1353" height = "500" alt="Write Register" align=center />

#### 9.Write Registers(Child Thread)
	
	ModbusReq.writeRegisters(mModbusMaster, new OnRequestBack<String>() {
                        @Override
                        public void onSuccess(String s) {
                            Log.e(TAG, "writeRegisters onSuccess " + s);
                        }
    
                        @Override
                        public void onFailed(String msg) {
                            Log.e(TAG, "writeRegisters onFailed " + msg);
                        }
                    },1,2,new short[]{211,52,34});

<img src="https://github.com/zgkxzx/Modbus4Android/blob/master/screenshot/write_registers.png" width = "1353" height = "500" alt="Write Registers" align=center />

#### 10.Destroy Modbus Instance

	master.destroy();
	
### Feedback

You have any questions to send email to me.Thanks.

* e-mail : zgkxzx@163.com
* gmail : my.own.diy@gmail.com

### Me & Throught

#### Simplicity is not simple.
	
