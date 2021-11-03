# GetFromTraining

#
#### Snackbar
```java
Snackbar snackbar;
View view = getActivity().findViewById(android.R.id.content);
snackbar = Snackbar.make(view, msg, Snackbar.LENGTH_INDEFINITE);
snackbar.setAction("Dismiss", v->{});
snackbar.getView().setAlpha(.5f);
snackbar.show();
```

#
#### SearchView

- R.menu.toolbar_menu.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
    <item
        android:id="@+id/searchMenu"
        android:icon="@drawable/search_icon"
        android:title="search"
        app:showAsAction="ifRoom"
        app:actionViewClass="android.widget.SearchView"/>
</menu>
```
- activity_main.xml
```xml
<androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:background="#BF0F69B1"
        android:minHeight="?attr/actionBarSize"
        android:theme="?attr/actionBarTheme"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

```
- MainActivity.java
```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    setSupportActionBar(findViewById(R.id.toolbar));
}

@Override
public boolean onCreateOptionsMenu(Menu menu) {
    getMenuInflater().inflate(R.menu.toolbar_menu, menu);
    return true;
}
```
- ItemListFragment.java
```java
@Override
public void onCreate(@Nullable Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    setHasOptionsMenu(true);
}

@Override
public void onCreateOptionsMenu(@NonNull Menu menu, @NonNull MenuInflater inflater) {
    super.onCreateOptionsMenu(menu, inflater);

    SearchManager searchManager= (SearchManager) getActivity().getSystemService(Context.SEARCH_SERVICE);
    SearchView searchView = (SearchView) menu.findItem(R.id.searchMenu).getActionView();
    searchView.setSearchableInfo(searchManager.getSearchableInfo(getActivity().getComponentName()));
    searchView.setIconifiedByDefault(true);
    searchView.setMaxWidth(Integer.MAX_VALUE);
    searchView.setOnQueryTextListener(new SearchView.OnQueryTextListener() {});
}
```

---

```
Copyright 2021 M. Fadli Zein
```