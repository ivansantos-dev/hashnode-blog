## Swift UI Preview - Nice to know

As I am learning how to create iOS, I have learn a thing or two (literally two things I want to share)

# Environment Variables
If you are using environment objects, you probably already faced this issue, where in the preview, it asks for the environment variable. All you gotta do is add environment object itn he PreviewProvider.
```Swift
struct ListView_Previews: PreviewProvider {
    static var previews: some View {
            ListView()
                .environmentObject(ListViewModel())44
    }
}
```

# Navigation View

If you are using Navigation View, and you are creating a new view, you will probably noticed that your navigation title does not display in the Live Preview. To fix that, all you need to do is add Navigation View in the PreviewProvider method, like so:

```Swift
struct NoWorkoutView_Previews: PreviewProvider {
    static var previews: some View {
        NavigationView {
            NoWorkoutView()
                .navigationTitle("Workout")
        }
    }
}

```