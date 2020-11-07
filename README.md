# lab4_4

Chuyển đối số đến một tuyến đường đã đặt tên

## Các bước làm
1. Xác định các đối số bạn cần chuyển
```class ScreenArguments {
  final String title;
  final String message;

  ScreenArguments(this.title, this.message);
}
```
2. Tạo một widget trích xuất các đối số
```
class ExtractArgumentsScreen extends StatelessWidget {
  static const routeName = '/extractArguments';

  @override
  Widget build(BuildContext context) {
    // Extract the arguments from the current ModalRoute settings and cast
    // them as ScreenArguments.
    final ScreenArguments args = ModalRoute.of(context).settings.arguments;

    return Scaffold(
      appBar: AppBar(
        title: Text(args.title),
      ),
      body: Center(
        child: Text(args.message),
      ),
    );
  }
}
```
3. Đăng ký widget trong bảng routes 
```
MaterialApp(
  routes: {
    ExtractArgumentsScreen.routeName: (context) => ExtractArgumentsScreen(),
  },
);
```
4. Điều hướng đến tiện ích con
``RaisedButton(
  child: Text("Navigate to screen that extracts arguments"),
  onPressed: () {
    
    Navigator.pushNamed(
      context,
      ExtractArgumentsScreen.routeName,
      arguments: ScreenArguments(
        'Extract Arguments Screen',
        'This message is extracted in the build method.',
      ),
    );
  },
),
```
5.
