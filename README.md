# HYSPagerView

Use case

struct ContentView: View {
    @State private var currentPage = 0
    @State var canDrag: Bool = true
    
    var body: some View {
        PagerView(pageCount: 3, canDrag: $canDrag, currentIndex: $currentPage) {
            VStack {
                Color.blue
                Button {
                    withAnimation {
                        currentPage = 2
                    }
                } label: {
                    Text("Toogle drag")
                }
            }
            VStack {
                Color.red
                Button {
                    canDrag.toggle()
                } label: {
                    Text("Toogle drag")
                }
            }
            VStack {
                ScrollView(.vertical, showsIndicators: false) {
                    ForEach(1..<100) { item in
                        Text("\(item)").foregroundColor(Color.red)
                            .frame(maxWidth: .infinity, maxHeight: 100)
                            .background(Color.green)
                    }
                }
                .frame(maxWidth: .infinity, maxHeight: .infinity)
                .background(Color.gray)
                
                Button {
                    canDrag.toggle()
                } label: {
                    Text("Toogle drag")
                }
            }
        }
    }
}
