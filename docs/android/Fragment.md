# Fragment


- Fragments
  - when is it created and destroyed?
  - setHasOptionMenu()
- Singleton Pattern
- Fragment Arguments
  - Starting an activity from a fragment
  - Fragment arguments
  - For the More Curious: Why Use Fragment Arguments? Why not just set an instance variable on the CrimeFragment when it is created?
  - Retaining fragments from desrtroying


A Fragment represents a reusable portion of your app's UI. A fragment defines and manages its own layout, has its own lifecycle, and can handle its own input events. 

Fragments cannot live on their own--they must be hosted by an activity or another fragment. The fragment’s view hierarchy becomes part of, or attaches to, the host’s view hierarchy.


- `onCreateView(inflater, container, savedInstanceState)`

**Fragment Life Cycle**
![Screenshot](img/fragment_lifecycle.png)


## ListFragment

Displays a list of items that are managed by an adapter, similar to ListActivity. It provides several methods for managing a list view, such as the onListItemClick() callback to handle click events.

## PreferenceFragmentCompat

Displays a hierarchy of Preference objects as a list. This is used to create a settings screen for your application.


# DialogFragment

- https://developer.android.com/reference/androidx/fragment/app/DialogFragment

Displays a floating dialog.

A DialogFragment is a special fragment subclass that is designeed for creating and hosting dialogs.

Strictly speaking, you do not need to host your dialog within a fragment, but doing so allows the [`FragmentManager`](https://developer.android.com/guide/fragments/fragmentmanager) to manage the state of the dialog and automatically restore the dialog when a configuration change occurs.

```kotlin
import androidx.fragment.app.DialogFragment;

public class MyDialogFragment extends DialogFragment {
	override fun onCreateView() {

	}

	override fun onViewCreaed() {

	}

	override fun onCreateDialog() {

	}

}

// Show dialog
FrgmentManager fm = getSupportFragmentManager()
val myDialogFragment = MyDialogFragment.newInstance()
myDialogFragment.show(fm, "my_dialog_fragment")
```

## LifeCycle
```shell
# on start
onAttach
onCreate
onCreateDialog
onCreateView
onActivityCreated
onStart
onResume


# on destroying
onPause
onStop
onDestroyView
onDestroy
onDetach
```



## Dialog
Dialog is a small window that prompts user to make a decision or enter additional information.

`Dialog` is the base class for dialogs, but you should avoid instantiating `Dialog` directly. Instead, user one of the following subclasses:
- AlertDialog
- DatePickerDialog
- TimePickerDIalog

These classes define style and structure for your dialog, but you should use a `DialogFragment` as a container for your dialog. The `DialogFragment` class provides all the controls you need to create the dialog and manage its appearance, instead of calling methods on the `Dialog` object.

# FragmentManager
Every FragmentActivity and its subclasses. such as AppCompatActivity, have access to the FragmentManager through `getSupportFragmentManager()`

Fragments can access host FragmentManager using `getParentFragmentManager()`

Fragments arte capable of hosting one or moree child fragments. Inside a fragment, you can get a refference to the FragmntManager that manages the fragment's childreen through `getChildFragmentManager()`


`<image src="https://developer.android.com/images/fragment_lifecycle.png" align=right>`

Represents a portion of user interface in an Activity.
Fragment class looks a lot like an Activity. It contains callback methods simillar to an Activity. In fact, if you're converting an existing Android application to use fragments, you might simply move code from your activity's callback methods into the respective callback methods of your fragment.

- **onCreate**: The system calls this when creating the fragment.
- **onCreateView**:
- **onPause**:

There are also a few subclasses that you might want to extend, instead of the base Fragment class:

```kotlin
class MyFragment : Fragment() {

    override fun onCreateView(
            inflater: LayoutInflater,
            container: ViewGroup?,
            savedInstanceState: Bundle?
    ): View {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.my_fragment, container, false)
    }
}
```


# FAQ
## setFragmentResult & setFragmentResultListener
# Reference
- https://developer.android.com/guide/fragments
- https://material.io/components/dialogs
- https://developer.android.com/guide/topics/ui/dialogs
- https://developer.android.com/guide/fragments/dialogs
- https://developer.android.com/reference/android/app/DialogFragment
- https://developer.android.com/reference/androidx/fragment/app/DialogFragment